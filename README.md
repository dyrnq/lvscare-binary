## Usage
```bash
curl -fsSL https://github.com/dyrnq/lvscare-binary/releases/download/v4.1.3/lvscare-v4.1.3.linux-amd64.tar.gz | tar -xvz -C /usr/local/bin/
```

```bash
lvscare care --vs 10.10.10.10:8443 --mode link --logger INFO --rs 192.168.27.11:6443 --rs 192.168.27.12:6443 --rs 192.168.27.13:6443 --health-insecure-skip-verify true --health-status 401,403
```

## ref
- <https://github.com/labring/lvscare>