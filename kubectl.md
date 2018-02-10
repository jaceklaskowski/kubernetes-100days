# kubectl &mdash; Kubernetes Command-Line Interface

`kubectl` is the command-line interface for [Kubernetes](https://kubernetes.io/).

```
$ kubectl get pod
No resources found.
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
