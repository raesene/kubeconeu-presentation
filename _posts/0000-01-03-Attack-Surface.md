<image src="/images/Attack-Surface.jpg"/>

Note: 

So the attack surface for a system is very important as it represents the ways in which an attacker can try to gain access to it.  The more attack surface, the more opportunities for the attacker to find a mis-configuration or vulnerability.

--

<image src="/images/shipwreck.jpg"/>

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
