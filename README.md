## Usage
```bash
latest_ver=$(curl -fsSL https://api.github.com/repos/dyrnq/lvscare-binary/releases/latest | jq -r '.tag_name')
if [ "$(uname -m)" = "x86_64" ]; then arch="amd64"; fi
if [ "$(uname -m)" = "aarch64" ]; then arch="arm64"; fi
DOWNLOAD_URL="https://github.com/dyrnq/lvscare-binary/releases/download/${latest_ver}/lvscare-${latest_ver}.linux-${arch}.tar.gz"
#DOWNLOAD_URL="${DOWNLOAD_URL/github.com/files.m.daocloud.io/github.com}"
DOWNLOAD_URL="${DOWNLOAD_URL/https/https://mirror.ghproxy.com/https}"
echo "DOWNLOAD_URL=${DOWNLOAD_URL}"
curl -fsSL $DOWNLOAD_URL | tar -xvz -C /usr/local/bin/
```

```bash
/usr/local/bin/lvscare version
```

```bash
/usr/local/bin/lvscare care \
--vs 10.10.10.10:8443 \
--mode link \
--logger INFO \
--rs 192.168.27.11:6443 \
--rs 192.168.27.12:6443 \
--rs 192.168.27.13:6443 \
--health-insecure-skip-verify true \
--health-status 401,403,200,201 \
--health-schem https \
--health-path "/livez" \
--interval 2
```

## ref
- <https://github.com/labring/lvscare>