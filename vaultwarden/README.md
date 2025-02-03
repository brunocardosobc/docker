# Vaultwarden - Docker Compose Setup

## 📌 Sobre

Este repositório fornece um **docker-compose.yml** para configurar e executar o **Vaultwarden**, uma implementação leve do Bitwarden compatível com Web Vault e aplicativos oficiais.

## 📦 Requisitos

- Docker instalado
- Docker Compose instalado
- Uma rede Docker externa chamada **npm-backend** (se ainda não existir, crie com `docker network create npm-backend`, conforme instruções em [https://github.com/brunocardosobc/docker/tree/main/nginx-proxy-manager](https://github.com/brunocardosobc/docker/tree/main/nginx-proxy-manager))

## 🚀 Configuração e Execução

1. Clone este repositório ou crie o arquivo **docker-compose.yml**.
2. Defina a variável de ambiente **VAULTWARDEN\_ADMIN\_TOKEN** no sistema ou em um arquivo `.env`.
3. Execute o comando para iniciar os containers:

```sh
docker-compose up -d
```

## 🔧 Configuração do Vaultwarden

O Vaultwarden será iniciado e exposto na porta **80**. Se precisar acessar o painel de administração, utilize a URL:

```
http://IPDOSERVIDOR/admin
```

E insira o token definido na variável **VAULTWARDEN\_ADMIN\_TOKEN**.

## 🛠️ Configuração Avançada

Caso deseje personalizar mais opções, você pode adicionar as seguintes variáveis de ambiente no `docker-compose.yml`:

```yaml
    environment:
      - SIGNUPS_ALLOWED=true   # Permitir registro de novos usuários
      - LOG_LEVEL=warn         # Ajustar o nível de log
      - DOMAIN=https://seu-dominio.com  # Definir domínio para SSL
```

## 📌 Persistência de Dados

Os dados do Vaultwarden serão armazenados localmente na pasta **./data** e montados dentro do container em **/data**.

Se quiser realizar backup, basta copiar o conteúdo da pasta `./data`.

## 📖 Referências

- [Repositório Oficial do Vaultwarden](https://github.com/dani-garcia/vaultwarden)
- [Documentação Oficial do Bitwarden](https://bitwarden.com/help/)

## 🔄 Parar e Remover os Containers

Para parar os containers, execute:

```sh
docker-compose down
```

Se desejar remover também os volumes:

```sh
docker-compose down -v
```


