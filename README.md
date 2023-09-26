<p align="center">
<img src="https://cwmkt.com.br/wp-content/uploads/2023/08/logo-github-cwmkt.svg" alt="DispZap Whats Marketing" width="240" />
<p align="center">Seja bem-vindo ao Guia de Instalação WUZAPI 🚀</p>
</p>
  
<p align="center">
<img src="https://whatsapp.com/favicon.ico" alt="WhatsAPP-logo" width="32" />
<span>Grupo WhatsaAPP: </span>
<a href="https://link.cwmkt.com.br/grupo-whats" target="_blank">Grupo</a>
</p>

<hr />
<hr />

<details>
<summary>Manual de Instalação Chatwoot</summary>

### Atualize sua máquina com os últimos pacotes

```bash
sudo apt update && apt upgrade -y
```

### Baixe o instalador automático do Chatwoot

```bash
wget https://get.chatwoot.app/linux/install.sh
```

### Execute a permisão no arquivo install.sh

```bash
chmod +x install.sh
```

### Inicie a instalação, digite "yes" para SSL, em seguida digite seu dominio e prossiga confimando com yes.
### Esse processo vai levar média ~ 15

  ```bash
./install.sh --install
  ```

Use as opções abaixo

yes

app.dominio.com.br

contato@dominio.com.br

yes para todos

### Alterando Idioma e ativando sua tela de cadastro

```bash
nano /home/chatwoot/chatwoot/.env
```

Altere a linha:

`DEFAULT_LOCALE=pt_BR` para `ENABLE_ACCOUNT_SIGNUP=true`

```bash
systemctl daemon-reload && systemctl restart chatwoot.target
```

Acesse: app.seudominio.com.br

Faça seu cadastro

### Habilitando configurações ocultas do Chatwoot no banco de dados PostgreSQL

```bash
sudo -i -u postgres psql
\c chatwoot_production
```

```bash
update installation_configs set locked = false;
```

```bash
\q
```

</details>

<details>
<summary>Manual de Instalação WUZAPI</summary>
  
### Instale as Dependências

```bash
sudo apt install git -y
```

```bash
sudo apt install golang-go
```

```bash
sudo apt install sqlite3
```

### Clone Repositório Oficial da WUZAPI

```bash
git clone https://github.com/hasanbasri1993/wuzapi
```

### Proxy Reverso

```bash
sudo apt install nginx -y
```

```bash
sudo rm /etc/nginx/sites-enabled/default
```

```bash
sudo nano /etc/nginx/sites-available/wuzapi
```

```bash
server {
  server_name wuzapi.seudominio.com.br;
  location / {
    proxy_pass http://127.0.0.1:9000;
    proxy_http_version 1.1;
    proxy_set_header Upgrade $http_upgrade;
    proxy_set_header Connection 'upgrade';
    proxy_set_header Host $host;
    proxy_set_header X-Real-IP $remote_addr;
    proxy_set_header X-Forwarded-Proto $scheme;
    proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
    proxy_cache_bypass $http_upgrade;
  }
   }
```

```bash
sudo ln -s /etc/nginx/sites-available/wuzapi /etc/nginx/sites-enabled
```

```bash
sudo apt-get install snapd -y
```

```bash
sudo snap install notes
```

```bash
sudo snap install --classic certbot
```

```bash
sudo certbot --nginx
```

```bash
sudo service nginx restart
```

### Configurando Conector com o Chatwoot

```bash
cd wuzapi
nano config.yaml
```

```bash
appName: NomeEmpresa
server: 
  host: wuzapi.seudominio.com.br
  port: 9000
chatwoot:
    baseUrl: https://urlchatwoot/app/accounts/numeroaccounts/inbox/numeroinbox
    accountToken: TokenChatwootProfile
    forceUpdateCwWebhook: false
```

### Criando sua Caixa de Entrada

### Url Webhook da API para colocar no Inbox do Chatwoot

```bash
http://wuzapi.seudominio.com.br/chatwoot
```

### Start API

```bash
go run .
```

### Crie um Usuário e token para iniciar Sessões

```bash
sqlite3 dbdata/users.db "insert into users ('name','token') values ('instancia','tokenaleatorio')"
```

### Gerar Qrcode

```bash
http://wuzapi.seudominio.com.br/login/?token=tokenaleatorio
```

### Informações Adicionais

Url da api 

http://wuzapi.seudominio.com.br

Url do swagger

http://wuzapi.seudominio.com.br/api

### Atualize sua máquina com os últimos pacotes

```bash
sudo apt update && apt upgrade -y
```

</details>

#### Acesse super Admin

https://app.seudominio.com.br/super_admin

Navegue até a opção > installation_configs

Navegue até a opção > installation_configs

```bash
LOGO
LOGO_THUMBNAIL
NOMES CHATWOOT:
```

### Alterando nomes na Plataforma

```bash
INSTALLATION_NAME
BRAND_NAME
TERMOS E POLITICA DE PRIVACIDADE
TERMS_URL
PRIVACY_URL
BRAND_URL
WIDGET_BRAND_URL
```



