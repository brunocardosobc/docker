# Docker Compose Collection

Este repositório contém uma coleção de arquivos docker-compose para diferentes configurações e ambientes.

## 📋 Sobre

Este repositório serve como um centralizador de arquivos docker-compose, facilitando o gerenciamento e a reutilização de configurações Docker em diferentes projetos.
Para facilitar a instalação do docker, executar o comando abaixo para instalação das dependências e docker/docker compose
```bash
sudo bash -c "$(curl -fsSL https://github.com/brunocardosobc/docker/raw/refs/heads/main/install-docker.sh)"
```

## 🚀 Como usar

1. Clone o repositório:
```bash
git clone https://github.com/seu-usuario/docker-compose-collection.git
```

2. Navegue até o diretório do serviço desejado
3. Execute o docker-compose:
```bash
docker-compose up -d
```

## 📁 Estrutura do Repositório

```
.
├── README.md
├── bind9-webmin/
├── cloudflare-tunnel/
├── duplicati/
└── rustdesk/
```

## 🤝 Contribuindo

1. Faça um Fork do projeto
2. Crie sua Feature Branch (`git checkout -b feature/NovaFeature`)
3. Commit suas mudanças (`git commit -m 'Adicionando nova feature'`)
4. Push para a Branch (`git push origin feature/NovaFeature`)
5. Abra um Pull Request

## 📝 Notas

- Certifique-se de ter o Docker e Docker Compose instalados em sua máquina
- Cada diretório contém seu próprio README com instruções específicas
- Verifique as variáveis de ambiente necessárias em cada compose file

## 📜 Licença

Este projeto está sob a licença MIT - veja o arquivo [LICENSE.md](LICENSE.md) para mais detalhes.
```
