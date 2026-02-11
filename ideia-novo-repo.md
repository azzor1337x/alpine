# Estrutura sugerida para o repositório alpine-homelab

> Copie cada seção para o respectivo arquivo no repositório.

---

## README.md

```md
# 🛠️ Homelab em Notebook Antigo com Alpine Linux 🚀

Este repositório documenta a transformação de um notebook antigo em um **homelab funcional** usando **Alpine Linux**.

## 💻 Hardware

- CPU: AMD C-60 (1.0 GHz)
- RAM: 8 GB DDR3
- Disco: 120 GB
- OS: Alpine Linux 3.21
- Kernel: Linux 6.12 LTS

## 📦 Serviços configurados

- 🔒 Unbound (DNS recursivo local)
- 🐳 Docker
- 🧭 Portainer
- 🧱 Pi-hole
- 🌐 DNS local
- 📊 btop
- ⚡ fastfetch (MOTD)

## 📁 Estrutura

```

services/
├── unbound.md
├── docker.md
├── pihole.md
└── portainer.md
network/
├── dns.md
└── hostname.md
system/
├── packages.md
└── motd-fastfetch.md
assets/
└── fastfetch.txt

```

## 📚 Documentação

- [Unbound](services/unbound.md)
- [Docker](services/docker.md)
- [Portainer](services/portainer.md)
- [Pi-hole](services/pihole.md)
- [DNS](network/dns.md)
- [Hostname](network/hostname.md)
- [Fastfetch no MOTD](system/motd-fastfetch.md)
```

---

## services/unbound.md

````md
# 🔒 Unbound DNS

Configuração de DNS recursivo local utilizando **Unbound** no Alpine Linux.

## Instalação

```sh
apk add unbound
````

## Objetivo

* Resolver DNS localmente
* Reduzir latência
* Aumentar privacidade

## Status

```sh
rc-service unbound status
```

````

---

## services/docker.md

```md
# 🐳 Docker

Instalação e uso do Docker no Alpine Linux.

## Instalação

```sh
apk add docker docker-cli docker-compose
rc-update add docker boot
service docker start
````

````

---

## services/portainer.md

```md
# 🧭 Portainer

Interface web para gerenciamento de containers Docker.

```sh
docker volume create portainer_data
docker run -d \
  -p 9000:9000 \
  --name portainer \
  --restart=always \
  -v /var/run/docker.sock:/var/run/docker.sock \
  -v portainer_data:/data \
  portainer/portainer-ce
````

````

---

## services/pihole.md

```md
# 🧱 Pi-hole

Bloqueador de anúncios integrado ao DNS local.

Executado via Docker e integrado com Unbound.
````

---

## network/dns.md

```md
# 🌐 DNS Local

Configuração de DNS local apontando para o Unbound.

Arquivo `/etc/resolv.conf`:

```

nameserver 127.0.0.1

```
```

---

## network/hostname.md

````md
# 🖥️ Hostname

Definição de hostname no Alpine Linux.

```sh
echo "alpine-homelab" > /etc/hostname
hostname alpine-homelab
````

````

---

## system/packages.md

```md
# 📦 Pacotes básicos

```sh
apk add btop htop curl git nano fastfetch
````

````

---

## system/motd-fastfetch.md

```md
# ⚡ fastfetch no MOTD

Exibição automática do fastfetch ao login.

Editar `/etc/profile`:

```sh
fastfetch
````

````

---

## assets/fastfetch.txt

```txt
(cole aqui o ASCII / output do fastfetch)
````
