# istio

```
istioctl-1-14-1 manifest generate -r 1-14-1 --component Base -f config/iop-base.yaml > charts/base/templates/config.yaml
istioctl-1-14-1 manifest generate -r 1-14-1 --component Cni -f config/iop-cni.yaml > charts/cni/templates/config.yaml
istioctl-1-14-1 manifest generate -r 1-14-1 --component Pilot -s "components.pilot.k8s.overlays[0].name=istiod-1-14-1" -f config/iop-pilot.yaml > charts/pilot/templates/config.yaml
istioctl-1-14-1 manifest generate -r 1-14-1 --component IngressGateways -f config/iop-igws.yaml > charts/igws/templates/config.yaml
istioctl-1-14-1 manifest generate -r 1-14-1 --component IngressGateways -f config/iop-ewgw.yaml > charts/ewgw/templates/config.yaml
```

```
cat charts/pilot/templates/config.yaml | yq ea '[.] | .[19] | .data.config' \
> charts/pilot/files/istio-sidecar-injector.raw
```

```
./samples/multicluster/gen-eastwest-gateway.sh --revision 1-14-1 --mesh mesh1 --cluster cluster1 --network network1
```
