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

### Instale as dependências

```bash
sudo apt install git -y
```

```bash
sudo apt install golang-go
```

```bash
sudo apt install sqlite3
```

### Clone repositório oficial da WUZAPI

```bash
git clone https://github.com/hasanbasri1993/wuzapi
```

```bash
cd wuzapi
nano config.yaml
```

```bash
appName: CWMKT
server: 
  host: IPVPS
  port: 9000
chatwoot:
    baseUrl: https://urlchatwoot/app/accounts/numeroaccounts/inbox/numeroinbox
    accountToken: TokenChatwoot
    forceUpdateCwWebhook: false
```

### Start API

```bash
go run .
```

### Comando token

```bash
sqlite3 dbdata/users.db "insert into users ('name','token') values ('instancia','tokenaleatorio')"
```

### Chamar qrcode

```bash
http://IPVPS:9000/login/?token=123456
```

### Url webhook do chatwoot

```bash
http://IPVPS:9000/chatwoot
```

### Informações adicionais

Url da api 

http://IPVPS:9000

Url do swagger

http://IPVPS:9000/api

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


