# istio

```
istioctl-1-14-1 manifest generate -r 1-14-1 --component Base -f config/istio/iop-base.yaml > ~/git/istio/base/config.yaml
istioctl-1-14-1 manifest generate -r 1-14-1 --component Cni -f config/istio/iop-cni.yaml > ~/git/istio/cni/config.yaml
istioctl-1-14-1 manifest generate -r 1-14-1 --component Pilot -s "components.pilot.k8s.overlays[0].name=istiod-1-14-1" -f config/istio/iop-pilot.yaml > ~/git/istio/pilot/config.yaml
istioctl-1-14-1 manifest generate -r 1-14-1 --component IngressGateways -f config/istio/iop-igws.yaml > ~/git/istio/igws/config.yaml
```
