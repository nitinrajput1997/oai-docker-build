# oai-docker-build

### Clone Repo
```bash
git clone --branch v1.4.0 https://gitlab.eurecom.fr/oai/cn5g/oai-cn5g-fed.git
cd oai-cn5g-fed
git checkout -f v1.4.0
```

### Synchronize all git submodules
```
./scripts/syncComponents.sh --nrf-branch v1.4.0 --amf-branch v1.4.0 \
                              --smf-branch v1.4.0 --spgwu-tiny-branch v1.4.0 \
                              --udr-branch v1.4.0 --udm-branch v1.4.0 \
                              --ausf-branch v1.4.0 --upf-vpp-branch v1.4.0 \
                              --nssf-branch v1.4.0 
```

### Build 5G Core Component Images 

##### AMF | SMF | VPP-UPF | NRF | UDM | UDR | NSSF | trf-gen-cn5g
```
docker build --target oai-amf --tag oai-amf:v1.4.0 \
--file component/oai-amf/docker/Dockerfile.amf.ubuntu \
component/oai-amf


docker build --target oai-smf --tag oai-smf:v1.4.0 \
  --file component/oai-smf/docker/Dockerfile.smf.ubuntu \
  component/oai-smf


docker build --target oai-nrf --tag oai-nrf:v1.4.0 \
--file component/oai-nrf/docker/Dockerfile.nrf.ubuntu \
component/oai-nrf


docker build --target oai-spgwu-tiny --tag oai-spgwu-tiny:v1.4.0 \
--file component/oai-upf-equivalent/docker/Dockerfile.ubuntu \
component/oai-upf-equivalent


docker build --target oai-ausf --tag oai-ausf:v1.4.0 \
--file component/oai-ausf/docker/Dockerfile.ausf.ubuntu \
component/oai-ausf


docker build --target oai-udm --tag oai-udm:v1.4.0 \
--file component/oai-udm/docker/Dockerfile.udm.ubuntu \
component/oai-udm


docker build --target oai-udr --tag oai-udr:v1.4.0 \
--file component/oai-udr/docker/Dockerfile.udr.ubuntu \
component/oai-udr


docker build --target oai-upf-vpp --tag oai-upf-vpp:v1.4.0 \
--file component/oai-upf-vpp/docker/Dockerfile.upf-vpp.ubuntu \
component/oai-upf-vpp


docker build --target oai-nssf --tag oai-nssf:v1.4.0 \
--file component/oai-nssf/docker/Dockerfile.nssf.ubuntu \
component/oai-nssf


docker build --target trf-gen-cn5g --tag trf-gen-cn5g:latest \
--file ci-scripts/Dockerfile.traffic.generator.ubuntu18.04 \
.
```

### Check Containers
```
docker ps -a
```
