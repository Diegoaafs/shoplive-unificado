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

2. **Inicie os containers:**
   ```bash
   docker compose up -d
   ```

3. **Acesse as aplicações:**
   - ShopLive: http://shoplive.local/
   - LiveOficial: http://liveoficial.local/live/principal

## 🔧 Configuração do Proxy

O Nginx atua como proxy reverso, direcionando as requisições para os containers apropriados com base na URL.

## ⚠️ Observações Importantes

- As aplicações utilizam PHP 5.6, que é uma versão legada
- O ambiente é configurado para desenvolvimento local
- HTTPS está desabilitado por padrão