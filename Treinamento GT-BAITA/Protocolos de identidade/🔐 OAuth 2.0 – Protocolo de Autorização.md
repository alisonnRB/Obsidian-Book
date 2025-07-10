O **OAuth 2.0** é um protocolo de autorização que permite que aplicações de terceiros (clientes) acessem recursos protegidos em nome de um usuário, sem precisar conhecer sua senha.

---

### 🔄 Fluxo: Authorization Code (código de autorização)

Esse é o **fluxo mais seguro** e recomendado para aplicações web e móveis que **possuem backend próprio**.

#### 🔁 Etapas:

1. **Usuário acessa o aplicativo cliente (PS)** e tenta realizar uma ação que exige autenticação.
    
2. O **cliente redireciona o navegador** do usuário para o **servidor de autorização (PI)**, com uma URL contendo os **parâmetros do protocolo OAuth 2.0**.
    
3. O usuário faz login e concede permissão.
    
4. O PI redireciona o usuário de volta ao cliente, **enviando um código de autorização** na URL.
    
5. O **cliente troca o código por um token de acesso** diretamente com o PI (com autenticação).
    

---

#### 📦 Exemplo de URL (Authorization Request)

https://auth.exemplo.com/oauth/authorize?response_type=code&client_id=app123&redirect_uri=https://meuapp.com/callback&scope=readwrite&state=abc123

- `response_type=code`: indica uso do Authorization Code Flow
    
- `client_id`: ID do app cliente registrado
    
- `redirect_uri`: onde o usuário será redirecionado após o login
    
- `scope`: permissões solicitadas (sem padronização rígida)
    
- `state`: valor aleatório para mitigar CSRF

### ⚠️ Escopos não padronizados

Um problema do OAuth 2.0 é que **não define um conjunto fixo de escopos (scopes)**.  
Cada PI (como Google, Facebook, etc.) define os seus próprios, o que dificulta interoperabilidade.

Exemplo:

- Google: `profile`, `email`, `calendar.read`
    
- GitHub: `repo`, `user`, `read:org`
    

---

## 🧭 Outros fluxos do OAuth 2.0

Além do **Authorization Code**, o OAuth define outros **3 fluxos principais**, voltados para contextos diferentes:

---

### 1️⃣ Implicit Flow _(desencorajado)_

- Tokens são enviados diretamente na URL de redirecionamento.
    
- Riscos de exposição em navegadores e logs.
    
- **Não recomendado atualmente.**
    

---

### 2️⃣ Resource Owner Password Credentials _(desencorajado)_

- O usuário informa **login e senha diretamente ao cliente**.
    
- Cliente troca por um token com o PI.
    
- Útil apenas em cenários altamente controlados (ex: apps legados internos).
    
- **Fere o princípio de confiança zero.**
    

---

### 3️⃣ Client Credentials

- Usado quando **não há usuário final**, apenas **comunicação entre servidores** (machine-to-machine).
    
- O cliente se autentica diretamente com o PI usando `client_id` + `client_secret`.
    
- Obtém um token para acesso a recursos protegidos do próprio cliente.
    

---

## ✅ Modernização: Authorization Code + PKCE

Hoje em dia, o **Authorization Code com PKCE** (Proof Key for Code Exchange) é o padrão recomendado até mesmo para apps móveis e single-page apps, pois elimina a necessidade de um `client_secret` seguro.

---

[[🧾 PS e PI — Conceitos Fundamentais]]

#Protocolo 