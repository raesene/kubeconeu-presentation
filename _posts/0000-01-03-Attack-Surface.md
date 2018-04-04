<image src="/images/Attack-Surface.jpg"/>

--

### Kubernetes Deployment Optons

<img src="/images/wordcloud.png" width="75%"/>


Note:

There are currently over 66 different flavours of k8s available (https://docs.google.com/spreadsheets/d/1LxSqBzjOxfGx3cmtZ4EbB_BGCxT_wlxW_xgHVVa23es/edit#gid=0), in addition to the option of spinning up the cluster manually.  This leads to probably one of the larger problems for k8s security, which is that you get the defaults that the cluster provider decided were appropriate from a security standpoint, and this is generally opaque to the end user.

On premises could be something like kubeadm or kismatic. Cloud base self-managed could be something like kops, cloud-based provider managed is more like GKE.

There are some big differences between quite lightweight installers, to full PAAS offerings like Openshift.

One of the challenges in reviewing "Kubernetes" is that this variety means that there are lots of different deployment mechanisms, which have different security options set by default.

--

# So Where does the cloud come in?

--

### Cloudy Clusters

* GKE
* ACS/AKS
* EKS
* OCP
* ...

--

# The importance of secure defaults!

--

### Other means of acquiring access - Github!

<img src="/images/github_config_exposed.png"/>
