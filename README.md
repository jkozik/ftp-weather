## Setup

1. Copy the secrets template:
```bash
   cp ftp-secrets.yaml.template ftp-secrets.yaml
```

2. Edit `ftp-secrets.yaml` with your actual passwords

3. Apply secrets:
```bash
   kubectl apply -f ftp-secrets.yaml
```

4. Deploy the FTP servers:
```bash
   kubectl apply -f ftp-pv-pvc.yaml
   kubectl apply -f ftp-chwcom-svc-dep.yaml
   kubectl apply -f ftp-nwcom-svc-dep.yaml
   kubectl apply -f ftp-sancap-svc-dep.yaml
   kubectl apply -f ftp-weewxrtlsdr-svc-dep.yaml
   kubectl apply -f ftp-sancapvueweewx-svc-dep.yaml
```

5. Test upload to a station (example: weewxrtlsdr — curl uses passive mode by default, so this exercises the PASV port range too):
```bash
   echo "test" > /tmp/test.txt
   curl -T /tmp/test.txt "ftp://weewxrtlsdr:<password>@192.168.100.208:30421/test.txt"
```
   Confirm the file landed on the NFS share under `weather-stations/weewxrtlsdr/`.
