---
icon: frontend
order: 0
---

# Svelte

O framework que será utilizado para o frontend deste projeto será o Svelte, usando como linguagem base o Typescript (mais informações consulte a documentação: https://svelte.dev/docs/introduction).

### Instalação do Svelte

#### Instalar os Pré-Requisitos

O framework necessita de um gerenciador de pacotes e do node.js para funcionar. O gerenciador utilizado neste trabalho é o npm. Para instalar ambos basta rodar no terminal:

```bash
sudo apt install nodejs
```

Isso instalará o Node.js e suas dependências, em conjunto com o gerenciador npm.

Para verificar se foi instalado com sucesso, verique as versões de ambos no terminal:

```bash
npm -v
node -v
```

#### Iniciar um projeto em Svelte

Esta etapa é necessária somente para a criação do projeto, não é preciso realizá-la caso já tenha um projeto Svelte aberto.

Para instalar o Svelte, vá para o diretório desejado para instalar o framework (neste projeto, o local destinato encontra-se no diretório chamado "framework").

Abra um terminal no mesmo diretório e execute o código:

```bash
npm create svelte@latest myapp
```

Nas configurações iniciais, informadas no próprio terminal onde se iniciou o projeto, escolha as opções:

```
├── Which Svelte app template?
    ├── Skeleton project
├── Add type checking with TypeScript?
    ├── Yes, using TypeScript syntax
├── Select additional options (use arrow keys/space bar)
    ├── Add Vitest for unit testing    #Adicionaremos uma biblioteca de teste para utilizar no projeto.

```

No resultado final, o diretório terá uma nova pasta chamada ```myapp```.

#### Rodando o projeto em localhost

No mesmo diretório onde foi iniciado o Svelte, execute no terminal:

```bash
cd myapp
npm install
npm run dev
```

Ao final da execução, surgirá um endereço local que, quando for acessado no navegador local, a aplicação será mostrada ao usuário.