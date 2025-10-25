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
```
