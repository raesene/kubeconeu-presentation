<img src="images/malicious-container.jpg"/>

--

# Increased Attack Surface

 * Container Filesystem Access {% fragment %}
 * "Internal" Network Position {% fragment %}
 * Kernel Attacks {% fragment %}

--

# Attacking Service Account Tokens

Note:  from demo notes, service account tokens can be very dangerous if RBAC isn't used as they're cluster admins.

--

<video src="/demo_videos/service-token.mp4"/>

--

# Leveraging Access in the Cloud

--

<video src="/demo_videos/awsmeta.mp4"/>

--

# The importance of secure defaults!

Note:

The most important point in the talk.  What the distribution considers a "secure default" isn't necessarily what you should.  It's vitally important to ensure that whatever mechanism you choose to use to deploy and manage Kubernetes chooses defaults you're happy with. Many distros still aren't shipping with RBAC enabled, so service tokens are privileged, or are shipping with exposed etcd/Kubelet settings.
