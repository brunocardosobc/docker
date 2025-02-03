---

## **Nginx Proxy Manager - Docker Compose**

Este repositório contém um **Docker Compose** para configurar e executar o **[Nginx Proxy Manager](https://github.com/NginxProxyManager/nginx-proxy-manager)**, uma interface gráfica para gerenciamento de proxies reversos com suporte a **Let's Encrypt**, múltiplos domínios e configuração simplificada.

---

## **📌 Recursos Principais**
✅ Interface gráfica para configurar **proxies reversos** facilmente  
✅ Suporte embutido para **SSL gratuito via Let's Encrypt**  
✅ Gerenciamento de múltiplos domínios e subdomínios  
✅ Controle de acesso com usuários e permissões  
✅ Logs detalhados e estatísticas de tráfego  

---

## **📦 Instalação e Uso**
### **1️⃣ Pré-requisitos**
Certifique-se de ter instalado:
- **Docker** e **Docker Compose**  
- Um servidor ou máquina com portas **80, 81 e 443** disponíveis  
- Acesso à Internet para baixar as imagens Docker  

### **Recomentaçao**
- Criar duas redes do docker especificas para o Nginx Proxy Manager (NPM) separando frontend de backend
    - Exemplo:
    ```bash
    docker network create npm-frontend
    docker network create npm-backend
    ```

### **2️⃣ Clonando o Repositório**
#### 📁 Estrutura do Diretório

```
.
├── data/
├── letsencrypt/
└── docker-compose.yml
```
```bash
git clone https://github.com/brunocardoso/nginx-proxy-manager.git
cd nginx-proxy-manager
```

### **3️⃣ Iniciando o Container**
Execute o seguinte comando para iniciar o serviço:
```bash
docker-compose up -d
```
Isso criará e iniciará o **Nginx Proxy Manager** em segundo plano.

---

## **⚙️ Configuração Inicial**
1. **Acesse o Painel Web**  
   Abra o navegador e vá até:
   ```
   http://SEU-IP:81
   ```
2. **Login Padrão**  
   - **Usuário:** `admin@example.com`  
   - **Senha:** `changeme`  

3. **Alteração da Senha**  
   Após o primeiro login, altere a senha padrão para maior segurança.

4. **Criando um Proxy Reverso**
   - Vá até a aba **Proxies**
   - Clique em **Add Proxy Host**
   - Configure o domínio e o destino interno
   - Habilite **SSL (Let's Encrypt)** se necessário

---

## **📂 Estrutura basica do Docker Compose**
```yaml
services:
  app:
    image: 'jc21/nginx-proxy-manager:latest'
    restart: unless-stopped
    ports:
      - '80:80'      # Porta HTTP
      - '81:81'      # Interface administrativa
      - '443:443'    # Porta HTTPS
    environment:
      DB_SQLITE_FILE: /data/database.sqlite
      DISABLE_IPV6: 'true'  # Desativa IPv6 se necessário
    volumes:
      - ./data:/data
      - ./letsencrypt:/etc/letsencrypt
```

### **📌 Explicação dos Parâmetros**
- **`image: jc21/nginx-proxy-manager:latest`** → Usa a versão mais recente do Nginx Proxy Manager
- **`restart: unless-stopped`** → Reinicia automaticamente o serviço, exceto se for manualmente parado
- **`ports`** → Define as portas usadas para acessar o serviço
- **`environment`** → Define configurações de ambiente, como banco de dados SQLite e suporte a IPv6
- **`volumes`** → Armazena dados e certificados SSL persistentes

---

## **🔧 Configuração Avançada**
Se precisar adicionar portas extras (exemplo: **Zabbix ou outros serviços**), edite o `docker-compose.yml`:
```yaml
    ports:
      - '9090:9090'  # Porta personalizada
      - '10051:10051'  # Exemplo: Zabbix Server
    networks:
      - npm-frontend
      - npm-backend

networks:
  npm-frontend
    external: true
  npm-backend
    external: true
```
Após a modificação, reinicie o serviço:
```bash
docker-compose down && docker-compose up -d
```

---

## **📜 Licença**
Este projeto segue a licença **MIT**, permitindo o uso livre e modificações conforme necessário.

---

## **📞 Suporte e Contribuições**
Se tiver dúvidas, sugestões ou melhorias, sinta-se à vontade para abrir uma **issue** ou enviar um **pull request**. 🚀

📩 Criado e mantido por **[Bruno Cardoso](https://github.com/brunocardosobc)**.

---