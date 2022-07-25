# istio

Initial scaffolding:
```
./bin/generate 1-14-2 Base > charts/base/templates/config.yaml
./bin/generate 1-14-2 Cni > charts/cni/templates/config.yaml
./bin/generate 1-14-2 Pilot > charts/pilot/templates/config.yaml
./bin/generate 1-14-2 IngressGateways > charts/igws/templates/config.yaml
./bin/generate 1-14-1 EastWestGateway > charts/ewgw/templates/config.yaml
```

```
cat charts/pilot/templates/config.yaml | yq ea '[.] | .[19] | .data.config' \
> charts/pilot/files/istio-sidecar-injector.raw
```

```
./samples/multicluster/gen-eastwest-gateway.sh --revision 1-14-1 --mesh mesh1 --cluster kube-01 --network network1
```
