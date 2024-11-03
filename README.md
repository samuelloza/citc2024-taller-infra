# citc2024-taller-infra



## Requisitos


### Docker
```
curl -fsSL https://get.docker.com -o install-docker.sh
sudo sh install-docker.sh

sudo systemctl enable docker.service
sudo systemctl enable containerd.service
```

### Usuario deploy
```
sudo adduser deploy
sudo usermod -aG docker deploy
sudo su - deploy

docker network create traefik-net


ssh-keygen -t ed25519 -C "YOUR-MAIL@mail.com"

cat ~/.ssh/id_ed25519
```

### Subir nuestra llava ssh
```
https://github.com/settings/tokens/new


```
