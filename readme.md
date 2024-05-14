# Biescloud
My personal docker-compose colleciton hosted on raspberry-pi

## setup
```
cd /srv
git clone https://github.com/MakerTim/biescloud

touch /srv/files/.env
# replace ... for passwords
echo HTA_MAR=... >> /srv/files/.env
echo HTA_TIM=... >> /srv/files/.env
echo HTA_LOT=... >> /srv/files/.env
echo HTA_RUR=... >> /srv/files/.env
sed -n '/^HTA_MAR/s/.*=//p' /srv/files/.env | openssl passwd -apr1 -stdin > /srv/files/.htpasswd-margret
sed -n '/^HTA_TIM/s/.*=//p' /srv/files/.env | openssl passwd -apr1 -stdin > /srv/files/.htpasswd-tim
sed -n '/^HTA_LOT/s/.*=//p' /srv/files/.env | openssl passwd -apr1 -stdin > /srv/files/.htpasswd-lotte
sed -n '/^HTA_RUR/s/.*=//p' /srv/files/.env | openssl passwd -apr1 -stdin > /srv/files/.htpasswd-rurik

cd /srv/files
docker compose up -d

cd /srv/vpn
docker comopse up -d
```
