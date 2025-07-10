
**OpenID Connect** é um protocolo de autenticação construído sobre o **OAuth 2.0**.  
Ele resolve a **falta de padronização de atributos de identidade** do usuário presente nas implementações puras de OAuth.

> Em vez de reinventar um protocolo, o OIDC **estende o OAuth 2.0** para incluir um mecanismo confiável de autenticação e fornecimento de dados de identidade.

---

### 🎯 Objetivos principais:

- Padronizar a **representação da identidade do usuário**.
    
- Permitir **autenticação federada** (ex: login com Google, Microsoft, etc.).
    
- Suportar **auto-registro** e descoberta de informações do usuário.
    
- Adicionar um novo tipo de token: o **ID Token**.
    

---

## 🔄 Tokens utilizados no OpenID Connect

Além dos tokens padrão do OAuth 2.0, o OIDC adiciona:

|Token|Descrição|
|---|---|
|`access_token`|Token usado para acessar APIs protegidas.|
|`refresh_token`|Token usado para renovar o `access_token`.|
|`id_token`|Token **JWT** contendo **informações de identidade do usuário**. Assinado digitalmente pelo PI.|

---

### 📦 Exemplo de URL de autenticação OpenID Connect

https://auth.exemplo.com/authorize?response_type=code&client_id=meu_app&redirect_uri=https://meuapp.com/callback&scope=openid profile email&state=xyz123

#### 🔍 Detalhes:

- `scope=openid`: **obrigatório** — indica uso de OpenID Connect.
    
- `profile`, `email`, etc: escopos adicionais que **padronizam os atributos** retornados.
    
- `state`: protege contra ataques de CSRF.
    
- `response_type=code`: indica uso do **Authorization Code Flow**.
    

---

## 📑 Escopos e Atributos Padrão

O OIDC define escopos que ativam conjuntos padronizados de atributos no `id_token` ou no _userinfo endpoint_:

| Escopo    | Atributos inclusos                                                                      |
| --------- | --------------------------------------------------------------------------------------- |
| `openid`  | Apenas o `sub` (subject identifier). Obrigatório para qualquer requisição OIDC.         |
| `profile` | `name`, `family_name`, `given_name`, `nickname`, `picture`, `gender`, `birthdate`, etc. |
| `email`   | `email`, `email_verified`                                                               |
| `address` | `address`                                                                               |
| `phone`   | `phone_number`, `phone_number_verified`                                                 |

---

## 🧾 Campos (`claims`) comuns do `id_token`

|Claim|Significado|
|---|---|
|`sub`|**Subject Identifier** — identificador único do usuário no PI.|
|`iss`|**Issuer** — URL do Provedor de Identidade (PI) que emitiu o token.|
|`aud`|**Audience** — quem deve aceitar esse token (normalmente o `client_id`).|
|`exp`|**Expiration** — timestamp de expiração do token (em segundos Unix).|
|`iat`|**Issued At** — quando o token foi emitido.|
|`auth_time`|Quando o usuário fez login (timestamp).|
|`nonce`|Valor aleatório usado para proteger contra replay attacks.|
|`acr`|**Authentication Context Class Reference** — nível de garantia da autenticação (ex: MFA).|
|`amr`|**Authentication Methods References** — métodos usados (ex: `pwd`, `otp`).|
|`azp`|**Authorized party** — qual cliente foi autorizado (caso `aud` tenha múltiplos).|
|`email`|E-mail do usuário (requer escopo `email`).|
|`name`, `given_name`, `family_name`, `picture`|Dados de perfil do usuário (requer escopo `profile`).|

---

🧪 Exemplo de `id_token` decodificado (payload)

{
  "iss": "https://auth.exemplo.com",
  "sub": "abc123",
  "aud": "client_xyz",
  "exp": 1720368230,
  "iat": 1720364630,
  "auth_time": 1720364600,
  "acr": "urn:mace:incommon:iap:silver",
  "amr": ["pwd", "otp"],
  "email": "usuario@exemplo.com",
  "email_verified": true,
  "name": "Usuário Exemplo"
}

---

[[🔐 OAuth 2.0 – Protocolo de Autorização]]

#Protocolo 