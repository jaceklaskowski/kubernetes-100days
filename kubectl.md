# kubectl &mdash; Kubernetes Command-Line Interface

`kubectl` is the command-line interface for [Kubernetes](https://kubernetes.io/).

```
$ kubectl get pod
No resources found.
```

## Configuration

```
$ kubectl -v=9 get pod
Config loaded from file /Users/jacek/.kube/config
```

## kubectl proxy

```
$ kubectl proxy
Starting to serve on 127.0.0.1:8001

$ http localhost:8001
HTTP/1.1 200 OK
Audit-Id: 0f57dd2e-2c00-4144-8ab8-dfb293855b5f
Content-Length: 2327
Content-Type: application/json
Date: Tue, 13 Feb 2018 19:50:36 GMT

{
    "paths": [
        "/api",
        "/api/v1",
        "/apis",
        "/apis/",
        "/apis/admissionregistration.k8s.io",
        "/apis/admissionregistration.k8s.io/v1beta1",
        "/apis/apiextensions.k8s.io",
        "/apis/apiextensions.k8s.io/v1beta1",
        "/apis/apiregistration.k8s.io",
        "/apis/apiregistration.k8s.io/v1beta1",
        "/apis/apps",
        "/apis/apps/v1",
        "/apis/apps/v1beta1",
        "/apis/apps/v1beta2",
        "/apis/authentication.k8s.io",
        "/apis/authentication.k8s.io/v1",
        "/apis/authentication.k8s.io/v1beta1",
        "/apis/authorization.k8s.io",
        "/apis/authorization.k8s.io/v1",
        "/apis/authorization.k8s.io/v1beta1",
        "/apis/autoscaling",
        "/apis/autoscaling/v1",
        "/apis/autoscaling/v2beta1",
        "/apis/batch",
        "/apis/batch/v1",
        "/apis/batch/v1beta1",
        "/apis/certificates.k8s.io",
        "/apis/certificates.k8s.io/v1beta1",
        "/apis/extensions",
        "/apis/extensions/v1beta1",
        "/apis/metrics.k8s.io",
        "/apis/networking.k8s.io",
        "/apis/networking.k8s.io/v1",
        "/apis/policy",
        "/apis/policy/v1beta1",
        "/apis/rbac.authorization.k8s.io",
        "/apis/rbac.authorization.k8s.io/v1",
        "/apis/rbac.authorization.k8s.io/v1beta1",
        "/apis/storage.k8s.io",
        "/apis/storage.k8s.io/v1",
        "/apis/storage.k8s.io/v1beta1",
        "/healthz",
        "/healthz/SSH Tunnel Check",
        "/healthz/autoregister-completion",
        "/healthz/etcd",
        "/healthz/ping",
        "/healthz/poststarthook/apiservice-openapi-controller",
        "/healthz/poststarthook/apiservice-registration-controller",
        "/healthz/poststarthook/apiservice-status-available-controller",
        "/healthz/poststarthook/bootstrap-controller",
        "/healthz/poststarthook/ca-registration",
        "/healthz/poststarthook/generic-apiserver-start-informers",
        "/healthz/poststarthook/kube-apiserver-autoregistration",
        "/healthz/poststarthook/rbac/bootstrap-roles",
        "/healthz/poststarthook/start-apiextensions-controllers",
        "/healthz/poststarthook/start-apiextensions-informers",
        "/healthz/poststarthook/start-kube-aggregator-informers",
        "/healthz/poststarthook/start-kube-apiserver-informers",
        "/logs",
        "/metrics",
        "/swagger-2.0.0.json",
        "/swagger-2.0.0.pb-v1",
        "/swagger-2.0.0.pb-v1.gz",
        "/swagger.json",
        "/swaggerapi",
        "/ui",
        "/ui/",
        "/version"
    ]
}

$ http localhost:8001/version
HTTP/1.1 200 OK
Content-Length: 269
Content-Type: application/json
Date: Tue, 13 Feb 2018 19:51:10 GMT

{
    "buildDate": "2018-01-31T22:30:55Z",
    "compiler": "gc",
    "gitCommit": "4ce7af72d8d343ea2f7680348852db641ff573af",
    "gitTreeState": "clean",
    "gitVersion": "v1.9.2-gke.1",
    "goVersion": "go1.9.2b4",
    "major": "1",
    "minor": "9+",
    "platform": "linux/amd64"
}

$ kubectl -v=9 version
I0213 20:51:43.283357   44432 loader.go:357] Config loaded from file /Users/jacek/.kube/config
I0213 20:51:43.285771   44432 round_trippers.go:417] curl -k -v -XGET  -H "Accept: application/json, */*" -H "User-Agent: kubectl/v1.9.3 (darwin/amd64) kubernetes/d283541" https://35.198.170.58/version
I0213 20:51:43.431557   44432 round_trippers.go:436] GET https://35.198.170.58/version 200 OK in 145 milliseconds
I0213 20:51:43.431586   44432 round_trippers.go:442] Response Headers:
I0213 20:51:43.431594   44432 round_trippers.go:445]     Content-Type: application/json
I0213 20:51:43.431600   44432 round_trippers.go:445]     Content-Length: 269
I0213 20:51:43.431607   44432 round_trippers.go:445]     Date: Tue, 13 Feb 2018 19:51:43 GMT
I0213 20:51:43.434173   44432 request.go:873] Response Body: {
  "major": "1",
  "minor": "9+",
  "gitVersion": "v1.9.2-gke.1",
  "gitCommit": "4ce7af72d8d343ea2f7680348852db641ff573af",
  "gitTreeState": "clean",
  "buildDate": "2018-01-31T22:30:55Z",
  "goVersion": "go1.9.2b4",
  "compiler": "gc",
  "platform": "linux/amd64"
}
Client Version: version.Info{Major:"1", Minor:"9", GitVersion:"v1.9.3", GitCommit:"d2835416544f298c919e2ead3be3d0864b52323b", GitTreeState:"clean", BuildDate:"2018-02-09T21:51:54Z", GoVersion:"go1.9.4", Compiler:"gc", Platform:"darwin/amd64"}
Server Version: version.Info{Major:"1", Minor:"9+", GitVersion:"v1.9.2-gke.1", GitCommit:"4ce7af72d8d343ea2f7680348852db641ff573af", GitTreeState:"clean", BuildDate:"2018-01-31T22:30:55Z", GoVersion:"go1.9.2b4", Compiler:"gc", Platform:"linux/amd64"}
```

## Verbose Mode

```
$ kubectl -v=9 get pod
I0210 22:29:50.514861   93045 loader.go:357] Config loaded from file /Users/jacek/.kube/config
I0210 22:29:50.523648   93045 round_trippers.go:417] curl -k -v -XGET  -H "Accept: application/json" -H "User-Agent: kubectl/v1.9.3 (darwin/amd64) kubernetes/d283541" https://35.198.170.58/api/v1/namespaces/default/pods?limit=500
I0210 22:29:50.664355   93045 round_trippers.go:436] GET https://35.198.170.58/api/v1/namespaces/default/pods?limit=500 200 OK in 140 milliseconds
I0210 22:29:50.664391   93045 round_trippers.go:442] Response Headers:
I0210 22:29:50.664404   93045 round_trippers.go:445]     Content-Length: 132
I0210 22:29:50.664414   93045 round_trippers.go:445]     Date: Sat, 10 Feb 2018 21:29:50 GMT
I0210 22:29:50.664422   93045 round_trippers.go:445]     Audit-Id: b85758a8-0869-48c1-ab6a-6ab1b14a5790
I0210 22:29:50.664429   93045 round_trippers.go:445]     Content-Type: application/json
I0210 22:29:50.664481   93045 request.go:873] Response Body: {"kind":"PodList","apiVersion":"v1","metadata":{"selfLink":"/api/v1/namespaces/default/pods","resourceVersion":"88356"},"items":[]}
No resources found.
```

## Installation (macOS)

[brew formula](http://formulae.brew.sh/formula/kubernetes-cli)

```
$ brew info kubernetes-cli
kubernetes-cli: stable 1.9.3 (bottled), HEAD
Kubernetes command-line interface
https://kubernetes.io/
/usr/local/Cellar/kubernetes-cli/1.9.2 (172 files, 65.3MB)
  Poured from bottle on 2018-01-22 at 21:57:53
/usr/local/Cellar/kubernetes-cli/1.9.3 (172 files, 65.4MB) *
  Poured from bottle on 2018-02-10 at 21:42:16
From: https://github.com/Homebrew/homebrew-core/blob/master/Formula/kubernetes-cli.rb
==> Dependencies
Build: go ✔
==> Options
--HEAD
	Install HEAD version
==> Caveats
Bash completion has been installed to:
  /usr/local/etc/bash_completion.d

zsh completions have been installed to:
  /usr/local/share/zsh/site-functions
```
