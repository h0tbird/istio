# istio

Initial scaffolding:
```
./bin/generate
```

Extract the sidecar-injector template:
```
cat charts/pilot/templates/generated.yaml | yq ea '[.] | .[17] | .data.config' \
> charts/pilot/files/istio-sidecar-injector.raw
```

```
./samples/multicluster/gen-eastwest-gateway.sh --revision 1-16-0 --mesh mesh1 --cluster kube-01 --network network1
```
