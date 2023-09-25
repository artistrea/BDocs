---
icon: container
order: 0
---

# Docker

O projeto utiliza o Docker para facilitar o desenvolvimento e a execução do projeto.

## Instalação Ubuntu

### Evitando conflitos

Verfique estar usando um entre:

- Ubuntu Lunar 23.04
- Ubuntu Kinetic 22.10
- Ubuntu Jammy 22.04 (LTS)
- Ubuntu Focal 20.04 (LTS)

E desinstale pacotes não oficiais, caso os tenha:

- docker.io
- docker-compose
- docker-doc
- podman-docker

O Docker Engine depende do `containerd` e do `runc`, mas os junta em um pacote só. Se você tiver instalado o `containerd` ou o `runc`, desinstale-os.

```bash
for pkg in docker.io docker-doc docker-compose podman-docker containerd runc; do sudo apt-get remove $pkg; done
```

### Instalando

Existem [diferentes maneiras de instalar](https://docs.docker.com/engine/install/ubuntu/#installation-methods) o Docker no Ubuntu. A mais simples é usar o apt.

1. Adicione o repositorio oficial do Docker:

```bash
# Add Docker's official GPG key:
sudo apt-get update
sudo apt-get install ca-certificates curl gnupg
sudo install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
sudo chmod a+r /etc/apt/keyrings/docker.gpg

# Add the repository to Apt sources:
echo \
  "deb [arch="$(dpkg --print-architecture)" signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  "$(. /etc/os-release && echo "$VERSION_CODENAME")" stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
```

2. Instale os pacotes necessários:

```bash
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

3. Verifique a instalação:

```bash
sudo docker run hello-world
```

E o Docker deve rodar a imagem e mostrar uma mensagem de sucesso:

```bash
Unable to find image 'hello-world:latest' locally
latest: Pulling from library/hello-world
719385e32844: Pull complete
Digest: sha256:4f53e2564790c8e7856ec08e384732aa38dc43c52f02952483e3f003afbf23db
Status: Downloaded newer image for hello-world:latest

Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (amd64)
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
 $ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker ID:
 https://hub.docker.com/

For more examples and ideas, visit:
 https://docs.docker.com/get-started/
```

## Pós Instalação

Se quiser rodar `docker` sem `sudo`, siga as [instruções do site oficial](https://docs.docker.com/engine/install/linux-postinstall/).

Verifique se a sessão da documentação em [primeira-entrega/postgresql](./postgresql.md) funciona com o Docker.
