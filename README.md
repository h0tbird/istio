# istio

```
istioctl-1-14-1 manifest generate -r 1-14-1 --component Base -f config/iop-base.yaml > charts/base/templates/config.yaml
istioctl-1-14-1 manifest generate -r 1-14-1 --component Cni -f config/iop-cni.yaml > charts/cni/templates/config.yaml
istioctl-1-14-1 manifest generate -r 1-14-1 --component Pilot -s "components.pilot.k8s.overlays[0].name=istiod-1-14-1" -f config/iop-pilot.yaml > charts/pilot/templates/config.yaml
istioctl-1-14-1 manifest generate -r 1-14-1 --component IngressGateways -f config/iop-igws.yaml > charts/igws/templates/config.yaml
```

```
sed -i 's/`/{{ printf "\\x60" }}/g' charts/pilot/templates/config.yaml
```

```
cat charts/pilot/templates/config.yaml | \
yq ea '[.] | .[] | select(.kind == "ConfigMap") | select(.metadata.name == "istio-sidecar-injector*") | \
.data.config' > charts/pilot/files/istio-sidecar-injector.raw
```
