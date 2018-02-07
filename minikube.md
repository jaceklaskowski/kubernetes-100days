# Minikube &mdash; Single-Node Local Kubernetes Cluster

**minikube** is a tool to set up a single-node Kubernetes cluster.

* enough for exploring most topics

Current version: Minikube [0.25.0](https://github.com/kubernetes/minikube/blob/v0.25.0/CHANGELOG.md#version-0250---1262018) with Kubernetes 1.9

## Documentation

1. https://kubernetes.io/docs/getting-started-guides/minikube/

## Installing minikube on macOS

Official docs: [Installing minikube](https://kubernetes.io/docs/tasks/tools/install-minikube/)

1. Install a Hypervisor, e.g. VirtualBox 5.2.6
2. [brew install kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-with-homebrew-on-macos)
3. [brew cask install minikube](https://github.com/kubernetes/minikube/releases)
    1. `brew cask reinstall minikube` to reinstall and **upgrade** minikube
    1. https://github.com/kubernetes/minikube/blob/v0.25.0/README.md

## Running minikube on macOS

```
$ which minikube
/usr/local/bin/minikube

$ minikube version
minikube version: v0.25.0

$ minikube start
Starting local Kubernetes v1.9.0 cluster...
Starting VM...
Getting VM IP address...
Moving files into cluster...
Downloading localkube binary
 162.41 MB / 162.41 MB [============================================] 100.00% 0s
 0 B / 65 B [----------------------------------------------------------]   0.00%
 65 B / 65 B [======================================================] 100.00% 0sSetting up certs...
Connecting to cluster...
Setting up kubeconfig...
Starting cluster components...
Kubectl is now configured to use the cluster.
Loading cached images from config file.

$ minikube status
minikube: Running
cluster: Running
kubectl: Correctly Configured: pointing to minikube-vm at 192.168.99.100

$ kubectl cluster-info
Kubernetes master is running at https://192.168.99.100:8443

To further debug and diagnose cluster problems, use 'kubectl cluster-info dump'.

$ kubectl version
Client Version: version.Info{Major:"1", Minor:"9", GitVersion:"v1.9.2", GitCommit:"5fa2db2bd46ac79e5e00a4e6ed24191080aa463b", GitTreeState:"clean", BuildDate:"2018-01-18T21:12:46Z", GoVersion:"go1.9.2", Compiler:"gc", Platform:"darwin/amd64"}
Server Version: version.Info{Major:"", Minor:"", GitVersion:"v1.9.0", GitCommit:"925c127ec6b946659ad0fd596fa959be43f0cc05", GitTreeState:"clean", BuildDate:"2018-01-26T19:04:38Z", GoVersion:"go1.9.1", Compiler:"gc", Platform:"linux/amd64"}

$ kubectl get nodes
NAME       STATUS    ROLES     AGE       VERSION
minikube   Ready     <none>    15d       v1.9.0

$ kubectl describe node minikube
Name:               minikube
Roles:              <none>
Labels:             beta.kubernetes.io/arch=amd64
                    beta.kubernetes.io/os=linux
                    kubernetes.io/hostname=minikube
Annotations:        alpha.kubernetes.io/provided-node-ip=192.168.99.100
                    node.alpha.kubernetes.io/ttl=0
                    volumes.kubernetes.io/controller-managed-attach-detach=true
Taints:             <none>
CreationTimestamp:  Mon, 22 Jan 2018 22:09:48 +0100
...

// Open http://192.168.99.100:30000 in the default browser
$ minikube dashboard
Opening kubernetes dashboard in default browser...

$ eval $(minikube docker-env)

$ docker ps
CONTAINER ID        IMAGE                                         COMMAND                  CREATED             STATUS              PORTS               NAMES
4f43c0e3addd        fed89e8b4248                                  "/sidecar --v=2 --lo…"   About an hour ago   Up About an hour                        k8s_sidecar_kube-dns-6777479f6b-5p6s2_kube-system_435953f7-09ee-11e8-a4fb-080027beab3f_3
a59c7ed907b8        k8s.gcr.io/k8s-dns-kube-dns-amd64             "/kube-dns --domain=…"   About an hour ago   Up About an hour                        k8s_kubedns_kube-dns-6777479f6b-5p6s2_kube-system_435953f7-09ee-11e8-a4fb-080027beab3f_3
e4138d046670        459944ce8cc4                                  "/dnsmasq-nanny -v=2…"   About an hour ago   Up About an hour                        k8s_dnsmasq_kube-dns-6777479f6b-5p6s2_kube-system_435953f7-09ee-11e8-a4fb-080027beab3f_3
03c7639e4a1b        k8s.gcr.io/kubernetes-dashboard-amd64         "/dashboard --insecu…"   About an hour ago   Up About an hour                        k8s_kubernetes-dashboard_kubernetes-dashboard-77d8b98585-95z8f_kube-system_43425126-09ee-11e8-a4fb-080027beab3f_3
f072c858c73d        gcr.io/google-containers/kube-addon-manager   "/opt/kube-addons.sh"    About an hour ago   Up About an hour                        k8s_kube-addon-manager_kube-addon-manager-minikube_kube-system_c4c3188325a93a2d7fb1714e1abf1259_3
033ca27a65c7        gcr.io/k8s-minikube/storage-provisioner       "/storage-provisioner"   About an hour ago   Up About an hour                        k8s_storage-provisioner_storage-provisioner_kube-system_9854d9af-ffb8-11e7-bd26-080027beab3f_4
b39b9a71a643        gcr.io/google_containers/pause-amd64:3.0      "/pause"                 About an hour ago   Up About an hour                        k8s_POD_kubernetes-dashboard-77d8b98585-95z8f_kube-system_43425126-09ee-11e8-a4fb-080027beab3f_3
39ac50871bc7        gcr.io/google_containers/pause-amd64:3.0      "/pause"                 About an hour ago   Up About an hour                        k8s_POD_storage-provisioner_kube-system_9854d9af-ffb8-11e7-bd26-080027beab3f_4
5c7f5b542eed        gcr.io/google_containers/pause-amd64:3.0      "/pause"                 About an hour ago   Up About an hour                        k8s_POD_kube-dns-6777479f6b-5p6s2_kube-system_435953f7-09ee-11e8-a4fb-080027beab3f_3
622b981f6066        gcr.io/google_containers/pause-amd64:3.0      "/pause"                 About an hour ago   Up About an hour                        k8s_POD_kube-addon-manager-minikube_kube-system_c4c3188325a93a2d7fb1714e1abf1259_3

$ minikube stop
Stopping local Kubernetes cluster...
Machine stopped.
```

## Inside minikube VM

```
$ minikube ssh
                         _             _
            _         _ ( )           ( )
  ___ ___  (_)  ___  (_)| |/')  _   _ | |_      __
/' _ ` _ `\| |/' _ `\| || , <  ( ) ( )| '_`\  /'__`\
| ( ) ( ) || || ( ) || || |\`\ | (_) || |_) )(  ___/
(_) (_) (_)(_)(_) (_)(_)(_) (_)`\___/'(_,__/'`\____)

$ uname -a
Linux minikube 4.9.13 #1 SMP Thu Oct 19 17:14:00 UTC 2017 x86_64 GNU/Linux

// Let’s look around and review the configuration (as if we were using the real Kubernetes head node)
// systemctl status kubelet
// /etc/systemd/system/kubelet.service.d/
$ systemctl status
● minikube
    State: running
     Jobs: 0 queued
   Failed: 0 units
    Since: Wed 2018-02-07 08:18:33 UTC; 46min ago
   CGroup: /
...

$ systemctl status localkube
● localkube.service - Localkube
   Loaded: loaded (/etc/systemd/system/localkube.service; enabled; vendor preset: enabled)
   Active: active (running) since Wed 2018-02-07 08:18:58 UTC; 45min ago
     Docs: https://github.com/kubernetes/minikube/tree/master/pkg/localkube
 Main PID: 3200 (localkube)
    Tasks: 16 (limit: 4915)
   Memory: 387.5M
      CPU: 3min 18.720s
   CGroup: /system.slice/localkube.service
           └─3200 /usr/local/bin/localkube --dns-domain=cluster.local --node-ip=192.168.99.100 --generate-certs=false --logtostderr=true --enable-dns=false

Feb 07 08:58:55 minikube localkube[3200]: store.index: compact 5229
Feb 07 08:58:55 minikube localkube[3200]: finished scheduled compaction at 5229 (took 360.927µs)
Feb 07 08:59:03 minikube localkube[3200]: E0207 08:59:03.130887    3200 healthcheck.go:317] Failed to start node healthz on 0: listen tcp: address 0: missing port in address
Feb 07 09:00:03 minikube localkube[3200]: E0207 09:00:03.131343    3200 healthcheck.go:317] Failed to start node healthz on 0: listen tcp: address 0: missing port in address
Feb 07 09:01:03 minikube localkube[3200]: E0207 09:01:03.131920    3200 healthcheck.go:317] Failed to start node healthz on 0: listen tcp: address 0: missing port in address
Feb 07 09:02:03 minikube localkube[3200]: E0207 09:02:03.132321    3200 healthcheck.go:317] Failed to start node healthz on 0: listen tcp: address 0: missing port in address
Feb 07 09:03:03 minikube localkube[3200]: E0207 09:03:03.133390    3200 healthcheck.go:317] Failed to start node healthz on 0: listen tcp: address 0: missing port in address
Feb 07 09:03:55 minikube localkube[3200]: store.index: compact 5411
Feb 07 09:03:55 minikube localkube[3200]: finished scheduled compaction at 5411 (took 508.142µs)
Feb 07 09:04:03 minikube localkube[3200]: E0207 09:04:03.134138    3200 healthcheck.go:317] Failed to start node healthz on 0: listen tcp: address 0: missing port in address

$ docker ps
CONTAINER ID        IMAGE                                         COMMAND                  CREATED              STATUS              PORTS               NAMES
57e7299e9762        fed89e8b4248                                  "/sidecar --v=2 --..."   About a minute ago   Up About a minute                       k8s_sidecar_kube-dns-6777479f6b-5p6s2_kube-system_435953f7-09ee-11e8-a4fb-080027beab3f_4
00fb16c937ef        k8s.gcr.io/k8s-dns-kube-dns-amd64             "/kube-dns --domai..."   About a minute ago   Up About a minute                       k8s_kubedns_kube-dns-6777479f6b-5p6s2_kube-system_435953f7-09ee-11e8-a4fb-080027beab3f_4
23dc5d200f28        k8s.gcr.io/kubernetes-dashboard-amd64         "/dashboard --inse..."   About a minute ago   Up About a minute                       k8s_kubernetes-dashboard_kubernetes-dashboard-77d8b98585-95z8f_kube-system_43425126-09ee-11e8-a4fb-080027beab3f_4
308baba19572        459944ce8cc4                                  "/dnsmasq-nanny -v..."   About a minute ago   Up About a minute                       k8s_dnsmasq_kube-dns-6777479f6b-5p6s2_kube-system_435953f7-09ee-11e8-a4fb-080027beab3f_4
d5739b03dd46        gcr.io/google-containers/kube-addon-manager   "/opt/kube-addons.sh"    About a minute ago   Up About a minute                       k8s_kube-addon-manager_kube-addon-manager-minikube_kube-system_c4c3188325a93a2d7fb1714e1abf1259_4
db2ada38e57d        gcr.io/google_containers/pause-amd64:3.0      "/pause"                 About a minute ago   Up About a minute                       k8s_POD_kubernetes-dashboard-77d8b98585-95z8f_kube-system_43425126-09ee-11e8-a4fb-080027beab3f_4
af0365a5313e        gcr.io/k8s-minikube/storage-provisioner       "/storage-provisioner"   About a minute ago   Up About a minute                       k8s_storage-provisioner_storage-provisioner_kube-system_9854d9af-ffb8-11e7-bd26-080027beab3f_5
7e2999a4df87        gcr.io/google_containers/pause-amd64:3.0      "/pause"                 About a minute ago   Up About a minute                       k8s_POD_kube-dns-6777479f6b-5p6s2_kube-system_435953f7-09ee-11e8-a4fb-080027beab3f_4
f2c3038f70e9        gcr.io/google_containers/pause-amd64:3.0      "/pause"                 About a minute ago   Up About a minute                       k8s_POD_storage-provisioner_kube-system_9854d9af-ffb8-11e7-bd26-080027beab3f_5
ada76588316e        gcr.io/google_containers/pause-amd64:3.0      "/pause"                 About a minute ago   Up About a minute                       k8s_POD_kube-addon-manager-minikube_kube-system_c4c3188325a93a2d7fb1714e1abf1259_4

$ exit
logout
```

## Caching Docker Images

```
// https://github.com/kubernetes/minikube/pull/2272
$ ./out/minikube cache add ubuntu:16.04 redis:3
$ ./out/minikube cache list
```
