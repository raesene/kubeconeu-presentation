<img src="images/external-attackers.jpg"/>

--

### External Network Visibility

* 2379/tcp      open  etcd
* 4194/tcp      open  cAdvisor
* (6|8)443/tcp  open  API Server
* 8080/tcp      open  Insecure API Server
* 10250/tcp     open  kubelet
* 10255/tcp     open  kubelet (Read Only)
* [various]     open  [Network plugins]

--

# Attacking the API Server

Note: 

Usually this shouldn't be something that can be easily attacked from an external perspective, unless you enable the insecure API port or disable authentication (but see the Tesla vulnerability for an example of that)

--

# Attacking etcd

Note:

We can used etcdctl to dump the contents of the database.  Importantly one of the things that etcd stores is all Kubernetes secrets are stored in clear text in etcd.  An attacker who can either get access to the etcd service or can get access to the underlying node can pwn all secrets.   A good secrets management post is at https://medium.com/on-docker/secrets-and-lie-abilities-the-state-of-modern-secret-management-2017-c82ec9136a3d#.k3yxv32o9

--

# Shodan & Friends

--

<img src="images/exposed_etcd.png"/>

Note:

Worth mentioning the etcd problem at this point... https://elweb.co/the-security-footgun-in-etcd/ which easily found loads of passwords and other items by just hitting unauthenticated etcd servers found via shodan. 

--

# Attacking the Kubelet

Note: 

The kubelet is a very interesting component from a security standpoint as it controls access to the container engine (e.g. Docker) running on the node.  There are generally 2 ports associated with the kubelet process.  10250/TCP is the read/write port, and 10255/TCP is the read-only port.  Prior to 1.5 all access to the kubelet was unauthenticated, so if you could see the port you could execute commands against it.  Since then it has been possible to restrict access, however many clusters still haven't implemented this protection.   Kubelet authorization is possible but the default is alwaysAllow https://kubernetes.io/docs/admin/kubelet-authentication-authorization/#kubelet-authentication
