---

---
[https://harrytang.xyz/blog/cloudflare-tunnel-alternative-k8s-ingress](https://harrytang.xyz/blog/cloudflare-tunnel-alternative-k8s-ingress)

![[SubPages/Pessoal/images/image 36.png]]

K8s Cloudflare Tunnel

## Introduction

Kubernetes Ingress is the most popular way to expose Kubernetes resources publicly. However, in some cases, you might prefer not to use an Ingress—for example, if you want to avoid load balancer costs or lack a publicly accessible IP address. Cloudflare Tunnel offers an ideal solution for these scenarios.

## Prerequisites

- A K8s cluster.
- Cloudflare Zero Trust.
- Cloudflare Tunnel client ([cloudflared](https://github.com/cloudflare/cloudflared)) installed.

## Step-by-step

1.  
	Log into Cloudflare account using cloudflared command
```plain text
cloudflared login

```
2.  
	Create a Tunnel
```plain text
cloudflared tunnel create TUNNEL_NAME

Tunnel credentials written to /root/.cloudflared/c068bf40-4a63-4de5-9ba7-3a565d4eae40.json.

```
3.     
    Create a secret to store the tunnel credentials
    With SealedSecret:
```plain text
kubectl -n K8S_NAMESPACE create secret generic tunnel-credentials --dry-run=client \
--from-file=credentials.json=/root/.cloudflared/c068bf40-4a63-4de5-9ba7-3a565d4eae40.json \
-o yaml | kubeseal --format=yaml > sealed-secret.yaml

```
    Or K8s normal secret:
```plain text
kubectl -n K8S_NAMESPACE create secret generic tunnel-credentials \
--from-file=credentials.json=/root/.cloudflared/c068bf40-4a63-4de5-9ba7-3a565d4eae40.json

```
4.  
	Chose you hostname & configure your DNS
	Suppose you want to expose your application at `app.mydomain.com`. In Cloudflare DNS, add a CNAME record named app pointing to your Cloudflare Tunnel hostname, e.g., `c068bf40-4a63-4de5-9ba7-3a565d4eae40.cfargotunnel.com`. You'll also need to configure the tunnel ingress with the desired hostname (app.mydomain.com) in the next step.
5.     
    Deploy and configure `cloudflared` using Helm
    With FluxCD:
```plain text
apiVersion: helm.toolkit.fluxcd.io/v2
kind: HelmRelease
metadata:
  name: cloudflared
  namespace: K8S_NAMESPACE
spec:
  interval: 24h
  chart:
    spec:
      chart: cloudflared
      version: '^0.1.1'
      sourceRef:
        kind: HelmRepository
        name: k8sonlab
        namespace: K8S_NAMESPACE
      interval: 24h
  values:
    cloudflare:
      tunnelName: TUNNEL_NAME
      tunnelId: c068bf40-4a63-4de5-9ba7-3a565d4eae40
      secretName: tunnel-credentials
      ingress:
        - hostname: app.mydomain.com
          service: http://app.K8S_NAMESPACE:3000
---
apiVersion: source.toolkit.fluxcd.io/v1
kind: HelmRepository
metadata:
  name: k8sonlab
  namespace: usa-idl-prod
spec:
  interval: 24h
  url: https://charts.ar80.eu

```
    Or with Heml CLI:
```plain text
helm repo add k8sonlab https://charts.ar80.eu
helm repo update

helm install cloudflared k8sonlab/cloudflared \
  --version 0.1.1 \
  --namespace K8S_NAMESPACE \
  --create-namespace \
  --set cloudflare.tunnelName=TUNNEL_NAME \
  --set cloudflare.tunnelId=c068bf40-4a63-4de5-9ba7-3a565d4eae40 \
  --set cloudflare.secretName=tunnel-credentials \
  --set cloudflare.ingress[0].hostname=app.mydomain.com \
  --set cloudflare.ingress[0].service=http://app.K8S_NAMESPACE:3000

```
6.  
	Verify
	You can visit `app.mydomain.com` to confirm that the tunnel is functioning properly.

## Conclusion

Using Cloudflare Tunnel to expose your Kubernetes services is straightforward, simple, and secure. Additionally, you also benefit from Cloudflare's features such as caching, CDN, and DDoS protection.

## References