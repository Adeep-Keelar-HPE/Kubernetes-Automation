# Single Master (Any Number of Wokers) Automation Steps Installation Spike 

## NOTE: No ETCD for now.

1. Check if MAC Address and Product_UUID are unique for the VMs
2. Install Run Time
 2.1 Prechecks -- Forwarding IPv4 and letting iptables see bridged traffic
 2.1.2 Comment /etc/fstab swap memory and swapoff -a. Verify with free
2.2 Install Container Runtime -- Containerd
1. wget https://github.com/containerd/containerd/releases/download/v1.7.20/containerd-1.7.20-linux-amd64.tar.gz
2. tar Cxzvf /usr/local containerd-1.7.20-linux-amd64.tar.gz
3. wget https://raw.githubusercontent.com/containerd/containerd/main/containerd.service -O /usr/lib/systemd/system/containerd.service
4. systemctl daemon-reload
5. systemctl enable --now containerd
6. Verify -- systemctl status containerd
7. wget https://github.com/opencontainers/runc/releases/download/v1.2.0-rc.2/runc.amd64
8. install -m 755 runc.amd64 /usr/local/sbin/runc
9. runc
10. mkdir -p /opt/cni/bin
11. wget https://github.com/containernetworking/plugins/releases/download/v1.5.1/cni-plugins-linux-amd64-v1.5.1.tgz
12. tar Cxzvf /opt/cni/bin cni-plugins-linux-amd64-v1.5.1.tgz 
13. mkdir /etc/containerd
14 containerd config default > /etc/containerd/config.toml
change line 125 systemcgroup = true
15 verify cgroupv2 --- stat -fc %T /sys/fs/cgroup/
16 systemctl restart containerd

-----
3. apt-get update
apt-get install -y apt-transport-https ca-certificates curl gpg
curl -fsSL https://pkgs.k8s.io/core:/stable:/v1.29/deb/Release.key | sudo gpg --dearmor -o /etc/apt/keyrings/kubernetes-apt-keyring.gpg
echo 'deb [signed-by=/etc/apt/keyrings/kubernetes-apt-keyring.gpg] https://pkgs.k8s.io/core:/stable:/v1.29/deb/ /' | sudo tee /etc/apt/sources.list.d/kubernetes.list
apt-get update
apt-get install -y kubelet kubeadm kubectl
apt-mark hold kubelet kubeadm kubectl
-----

(Without HA --> skip this part) Do this only on the master node.
4.
