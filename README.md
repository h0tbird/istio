# istio

```
./bin/generate 1-14-1 Base > charts/base/templates/config.yaml
./bin/generate 1-14-1 Cni > charts/cni/templates/config.yaml
./bin/generate 1-14-1 Pilot > charts/pilot/templates/config.yaml
./bin/generate 1-14-1 IngressGateways > charts/igws/templates/config.yaml
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
