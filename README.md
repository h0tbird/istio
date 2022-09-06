# istio

Initial scaffolding:
```
./bin/generate 1-15-0 Base > charts/base/templates/generated.yaml
./bin/generate 1-15-0 Cni > charts/cni/templates/generated.yaml
./bin/generate 1-15-0 Pilot > charts/pilot/templates/generated.yaml
./bin/generate 1-15-0 IngressGateways > charts/igws/templates/generated.yaml
./bin/generate 1-15-0 EastWestGateway > charts/ewgw/templates/generated.yaml
```

Extract the sidecar-injector template:
```
cat charts/pilot/templates/generated.yaml | yq ea '[.] | .[15] | .data.config' \
> charts/pilot/files/istio-sidecar-injector.raw
```

```
./samples/multicluster/gen-eastwest-gateway.sh --revision 1-15-0 --mesh mesh1 --cluster kube-01 --network network1
```
