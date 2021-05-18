# Deploy SISRECLEDGER

Pré requisitos

- [Docker](https://www.docker.com/)
- [docker-compose](https://docs.docker.com/compose/)

Dependências

- Banco de dados MySQL

## Instalação do Docker e docker-compose 

Para instalar o Docker no **Ubuntu** , basta utilizar o comando abaixo.
```
curl -fsSL https://get.docker.com | sh && \
sudo usermod -aG docker ubuntu && \
sudo reboot
```

Quando o server reiniciar, instale o docker-compose com o comando abaixo.
```
sudo curl -L "https://github.com/docker/compose/releases/download/1.28.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose && \
sudo chmod +x /usr/local/bin/docker-compose
```

## Deploy da aplicação

### 1) Estrutura de diretórios

Segue a estrutura de diretórios que o projeto deve seguir.

> .  
> ├── docker-compose.yaml  
> ├── Totum.API  
> └── Totum.FRONT

### 2) Variáveis de ambiente

Ambos códigos fonte (front e back-end), possuem variáveis de ambiente (credenciais, URL's, tokens, senhas, etc) que devem ser passadas num arquivo chamado **.env**

Esse arquivo dentro de suas respectivas pastas.

> .  
> ├── docker-compose.yaml  
> ├── Totum.API  
> │   └── .env  
> └── Totum.FRONT  
>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└── .env  


### 3) Deploy

Para subir a aplicação (front e back-end), basta ir até a raiz do projeto (onde o arquivo *docker-compose.yaml* está) e utilizar o seguinte comando:

```
docker-compose -p sisrec up -d --build
```

### 4) Utilizando a aplicação

Por padrão, a API está disponível na porta **3349** e o front na porta **80**.

### 5) Parando a aplicação

Para parar, basta navegar até a raiz do projeto e utilizar o seguinte comando.

```
docker-compose down
```

## Banco de dados

Esse passo é opcional. Serve apenas para ambientes de testes.

Para popular um banco MySQL novo com dados para teste (CEGS, usuário admin, etc), utilize o comando abaixo, após subir o projeto.

```
docker exec -it sisrec_api_1 adonis seed
```
