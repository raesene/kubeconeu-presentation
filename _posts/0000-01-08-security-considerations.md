<img src="images/key-security-considerations.jpg" />

--

## 1. Insecure Port

```
--insecure-port=0
--insecure-bind-address - Not Set
```


Note: 

The insecure port (typically 8080) is still used by some distributions and in at least one case, it's bound to a network interface that faces into the cluster (ACS), which means any user of the cluster can access it and execute commands.

--

## 2. Control Access to the Kubelet

```
--anonymous-auth=false
--authorization-mode - Not set to "AlwaysAllow"
--read-only-port=0
--cadvisor-port=0
```

--

## 3. Control Access to etcd

```
--client-cert-auth=true
--auto-tls=false
--peer-client-cert-auth=true
--peer-auto-tls=false
```

--

## 4. Restrict Service Token Use

--

## 5. Restrict Privileged Containers

--

## 6. API Server Authentication

```
--anonymous-auth=false
--basic-auth-file - Not Set
--token-auth-file - Not Set
```

Note:

There's 3 internal ways that k8s can authenticate users as well as referrring to an external service.  All three suffer some problems.  Basic and token authentication have the problem that they are static credentials which are held in the clear on the API server (and are also likely to be held on the clear on the clients too).  Also they're relatively inflexible (require API server retstart to change).  All in all not a great option.

Certificate authentication has some advantages in this regard, however there's currently no support for certificate revokation, so a compromised credential cannot easily be invalidatd.  Also within k8s the facilities for managing certificate are fairly basic.

Important point is "what are we authenticating?".  There's obviously the point of users of the cluster, however we're also authenticating the various components of the cluster (e.g. the scheduler needs to be able to talk to the Kubelet to schedule pods).  Additionally there's the possibility of a pod wanting to access the API server, via service tokens.

This particular concept causes one of the areas where cluster security can provide an unexpected, unpleasant, surprise (https://hackernoon.com/capturing-all-the-flags-in-bsidessf-ctf-by-pwning-our-infrastructure-3570b99b4dd0) .  Lets look at a cluster which has a container spun up on it and the service account token that gets automounted intot the container.

--


## 7. API Server Authorisation

```
--authorization-mode=RBAC
```


Note:

Once you've got authenticated users the question of what they're allowed to do becomes relevant.  One of the weaknesses of earlier distributions of K8s is that they tended not to implement any significant level of authorisation, so an attacker who gains access to a cluster authentication token or credential, gets full-cluster access.

An important point to note about the k8s approach to authorisation is that it's cumulative, so if you have multiple authorisation mechanisms enabled and any one of the mechanisms provides access, access is provided.  This can create the possibility of nasty surprises...

RBAC is generally considered the way authorisation will be handled going forward.  It does introduce, however, some complexity to managing a cluster.  For example on a kubeadm 1.6 cluster, there are 40 cluster roles created by default.

Also due to K8s not managing user identity, questions like "who has cluster-admin rights" become pretty difficult to answer.  For example if a certificate is created froma trusted CA with the system:masters group assigned, there's nothing within k8s that tracks the lifecycle of that certificate.

--

## 8. PodSecurityPolicy

--

## 9. NetworkPolicy

--

## 10. Regular Upgrades!

-- 

## Honourable Mention - Cloud Rights