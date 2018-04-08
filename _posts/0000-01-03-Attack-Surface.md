<image src="/images/Attack-Surface.jpg"/>

Note: 

So the attack surface for a system is very important as it represents the ways in which an attacker can try to gain access to it.  The more attack surface, the more opportunities for the attacker to find a mis-configuration or vulnerability.

--

### Kubernetes Deployment Optons

<img src="/images/wordcloud.png" width="75%"/>


Note:

There are currently over 66 different flavours of k8s available (https://docs.google.com/spreadsheets/d/1LxSqBzjOxfGx3cmtZ4EbB_BGCxT_wlxW_xgHVVa23es/edit#gid=0), in addition to the option of spinning up the cluster manually.  This leads to probably one of the larger problems for k8s security, which is that you get the defaults that the cluster provider decided were appropriate from a security standpoint, and this is generally opaque to the end user.

On premises could be something like kubeadm or kismatic. Cloud base self-managed could be something like kops, cloud-based provider managed is more like GKE.

There are some big differences between quite lightweight installers, to full PAAS offerings like Openshift.

One of the challenges in reviewing "Kubernetes" is that this variety means that there are lots of different deployment mechanisms, which have different security options set by default.

--

# Managed vs Unmanaged

Note:

Managed clusters have advantages in that the attack surface is smaller (i.e. if you have no access to the underlying platform, nor does an attacker who is masquerading as you) but also have disadvantages in that you are generally stuck with the settings chosen by the cluster deployment mechanism.

--

# Cloudy Clusters

Note:

Cloud based deployments are increasingly common.  They change things from an attack surface perspective as a) the cloud service management methods (e.g. AWS portal, awscli) are part of your attack surface.  Also the consequences of compromise can be worse (it's not just your cluster that gets compromised, it's the whole cloud setup)

--

# The importance of secure defaults!

Note:

The most important point in the talk.  What the distribution considers a "secure default" isn't necessarily what you should.  It's vitally important to ensure that whatever mechanism you choose to use to deploy and manage Kubernetes chooses defaults you're happy with. Many distros still aren't shipping with RBAC enabled, so service tokens are privileged, or are shipping with exposed etcd/Kubelet settings.

--

### Other means of acquiring access - Github!

<img src="/images/github_config_exposed.png"/>
