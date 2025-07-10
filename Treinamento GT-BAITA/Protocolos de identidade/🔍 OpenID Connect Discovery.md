O **OpenID Connect Discovery** é um mecanismo que permite que os **provedores de serviço (PS)** descubram, de forma **automática**, a configuração de um **Provedor de Identidade (PI)**, sem necessidade de configuração manual.

Ele define um **endpoint padrão** que expõe metadados sobre o PI e o que ele suporta:

---

### 📌 Endpoint de descoberta:

GET /.well-known/openid-configuration

>Esse endpoint retorna um **JSON de configuração**, que descreve todas as rotas, capacidades e regras do Provedor de Identidade.

---

📋 Exemplo de resposta

{
  "issuer": "https://auth.exemplo.com",
  "authorization_endpoint": "https://auth.exemplo.com/authorize",
  "token_endpoint": "https://auth.exemplo.com/token",
  "userinfo_endpoint": "https://auth.exemplo.com/userinfo",
  "jwks_uri": "https://auth.exemplo.com/.well-known/jwks.json",
  "response_types_supported": ["code", "id_token", "token id_token"],
  "subject_types_supported": ["public"],
  "scopes_supported": ["openid", "profile", "email"],
  "claims_supported": ["sub", "name", "email", "picture", "acr"]
}

---

### ✅ Benefícios do Discovery:

- Permite **autoconfiguração dinâmica** de clientes OAuth/OIDC.
    
- Exibe:
    
    - Endpoints (`authorize`, `token`, `userinfo`, etc.)
        
    - **Escopos disponíveis** (`openid`, `email`, `profile`...)
        
    - **Tipos de fluxos** suportados (`authorization_code`, `implicit`, etc.)
        
    - **Claims disponíveis** no `id_token` ou no `/userinfo`
        
    - Chaves públicas (`jwks_uri`) para validação de tokens

---

## 📥 Endpoint  `/userinfo`

- OpenID Connect O **OpenID Connect** define um endpoint padrão chamado **`/userinfo`**, usado para obter informações adicionais sobre o usuário autenticado.

[[🧠 OpenID Connect (OIDC)]]

#Protocolo 