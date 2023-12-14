# Relatório de Implantação

## Objetivo: 

O presente relatório tem por objetivo instruir o usuário acerca do passo a passo de implantação do sistema gerenciador de materiais para um laboratório didático, bem como seus requisitos de hardware e software. 

## Requisitos: 

- Conexão com a internet (no momento de instalação de dependências) 
- Computador com sistema operacional Ubuntu (Lunar, Kinetic, Jammy ou Focal) 

## Instalando dependências 

### Docker: 

O projeto por nós construído utiliza o Docker no intuito de facilitar a implantação do sistema e o seu desenvolvimento. Para fazer a instalação, inicialmente desinstale pacotes não oficiais,  caso  os  tenha:  docker.io;  docker-compose;  docker-doc;  podman-docker.  Se  você estiver com containerd ou o runc, também desinstale. Para isso, rode o comando: 
```bash
for pkg in docker.io docker-doc docker-compose podman-docker containerd runc; do sudo apt-get remove $pkg; done 
```
Partindo para a instalação, utilizaremos o apt. Adicione o repositório oficial do docker: 

```bash
# Add Docker's official GPG key:
sudo apt-get update
sudo apt-get install ca-certificates curl gnupg
sudo install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o
/etc/apt/keyrings/docker.gpg
sudo chmod a+r /etc/apt/keyrings/docker.gpg

# Add the repository to Apt sources:
echo \
"deb [arch="$(dpkg --print-architecture)" signed-by=/etc/apt/keyrings/docker.gpg]
https://download.docker.com/linux/ubuntu \
"$(. /etc/os-release && echo "$VERSION_CODENAME")" stable" | \
sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
```
Instale os pacotes necessários: 
```bash
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin 
```
Verifique a instalação: 
```bash
sudo docker run hello-world
```
E o docker deve rodar a imagem e mostrar uma mensagem de sucesso: 
```bash
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

### Flask:

Utilize o pip, gerenciador de pacotes Python, para instalar o Flask: 
```bash
pip install Flask
```
Para verificar se foi instalado com sucesso, rode: 
```bash
flask --version
```
Esse comando deve retornar a versão instalada. Se retornar uma mensagem de erro, possivelmente houve um problema com a instalação. 

Para executar o aplicativo Flask (iniciar o servidor flask), rode o comando:  
```bash
python3 -m flask --app src/app run --debug
```
Para parar o servidor, aperte `Ctrl + C`. 

### Node: 

Recomenda-se o uso do Node 21. Para instalá-lo, basta rodar: 
```bash
sudo apt install nodejs
```
Para verificar a instalação, rode: 
```bash
nodejs -v 
```
Se retornar a versão node instalada, está tudo certo com a instalação.  Instale também o gerenciador de pacotes node, o npm: 
```bash
sudo apt install npm
```
## Rodando o projeto

### Banco de dados 

Abra um terminal e execute: 
```bash
docker-compose up 
```
Para reiniciar o banco de dados do zero, limpe os volumes do docker, executando: 
```bash
docker-compose down --volumes
```
### Frontend 

Para rodar o frontend, primeiro instale os pacotes necessários: 
```bash
cd frontend
npm install 
```
E então rode o projeto:  
```bash
npm run dev
```
### Backend 

Para rodar o Backend, instale os pacotes necessários: 
```bash
cd api
pip install -r requirements.txt 
```
E então rode o projeto: 
```bash
python3 -m flask --app src/app run --debug
```
