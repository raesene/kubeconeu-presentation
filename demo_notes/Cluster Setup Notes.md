Cluster Setup Notes
--

So to set a cluster up for the demo's we need to break various things to demonstrate possible security issues.

Starting from a base Kubeadm 1.9 installation, with 3 Nodes (one master two minions)

If possible use the IP addresses

knode1 - 192.168.200.10
knode2 - 192.168.200.11
knode3 - 192.168.200.12
dregistry - 192.168.200.50

--
To setup the guestbook example we need to pull and tag some images and push to the dregistry host

you'll need to edit /etc/docker/daemon.json to add an entry for the insecure registry per https://docs.docker.com/registry/insecure/



Adding vulnerabilities
--

To sort out the kubelet we need to edit /etc/systemd/system/kubelet.service.d/10-kubeadm.conf
--anonymous-auth=true  --authorization-mode=AlwaysAllow --cadvisor-port=4194