# Ambiente de Desenvolvimento Live

Este projeto configura um ambiente de desenvolvimento que integra duas aplicações PHP legadas (ShopLive e LiveOficial) usando Docker e Nginx como proxy reverso.

## 📋 Pré-requisitos

- Docker
- Docker Compose
- Git

## 🗂 Estrutura do Projeto

```
.
├── docker/             # Arquivos Docker
├── docker-compose.yml  # Configuração dos containers
├── nginx-proxy.conf    # Configuração do proxy reverso
└── README.md          # Este arquivo
```

## 🚀 Serviços

O projeto consiste em três serviços principais:

1. **app-shoplive** (porta 8080)
   - Aplicação ShopLive
   - PHP 5.6 + Nginx
   - Configurações específicas para o ambiente ShopLive

2. **app-liveoficial** (porta 8081)
   - Aplicação LiveOficial
   - PHP 5.6 + Nginx
   - Configurações específicas para o ambiente LiveOficial

3. **nginx-proxy** (porta 80)
   - Proxy reverso
   - Unifica o acesso às aplicações através da porta 80
   - Gerencia o roteamento entre as aplicações

## 🛠 Como Usar

1. **Clone os repositórios necessários:**
   ```bash
   git clone [url-do-repositório-shoplive] ../shoplive
   git clone [url-do-repositório-liveoficial] ../liveoficial
   ```

2. **Configure os virtualhosts (Docker Desktop):**

   Os virtualhosts precisam ser configurados no arquivo de hosts do seu sistema para resolver os domínios locais.

   ### Linux/Mac: Editar `/etc/hosts`
   ```bash
   sudo nano /etc/hosts
   ```
   
   Adicione as seguintes linhas:
   ```
   127.0.0.1  shoplive.local
   127.0.0.1  liveoficial.local www.liveoficial.local
   ```
   
   Salve o arquivo (Ctrl+O, Enter, Ctrl+X no nano).

   ### Windows: Editar `C:\Windows\System32\drivers\etc\hosts`
   1. Abra o Notepad como Administrador
   2. Vá para **Arquivo** → **Abrir** e navegue até:
      ```
      C:\Windows\System32\drivers\etc\hosts
      ```
   3. Adicione as linhas:
      ```
      127.0.0.1  shoplive.local
      127.0.0.1  liveoficial.local www.liveoficial.local
      ```
   4. Salve o arquivo

   ### Verificar configuração
   ```bash
   ping shoplive.local
   ping liveoficial.local
   ```

3. **Inicie os containers:**
   ```bash
   docker compose up -d
   ```

4. **Acesse as aplicações:**
   - ShopLive: http://shoplive.local/
   - LiveOficial: http://liveoficial.local/live/principal

## 🔧 Configuração do Proxy

O Nginx atua como proxy reverso, direcionando as requisições para os containers apropriados com base na URL.

## ⚠️ Observações Importantes

- As aplicações utilizam PHP 5.6, que é uma versão legada
- O ambiente é configurado para desenvolvimento local
- HTTPS está desabilitado por padrão