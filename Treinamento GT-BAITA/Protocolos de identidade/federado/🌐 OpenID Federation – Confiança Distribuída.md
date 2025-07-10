**OpenID Federation** é uma extensão do OpenID Connect que tem como principal objetivo **resolver o problema da confiança entre participantes de uma federação** de forma **descentralizada e escalável**.

---

### 🔒 Problema com o modelo tradicional (SAML)

Nos modelos baseados em **SAML**, a confiança é geralmente **centralizada**, com todas as entidades configuradas diretamente pela federação (como se fosse uma autoridade central).

[ PI ] ←→ [ Federação Central ] ←→ [ PS ]

Isso gera:

- Gargalos operacionais,
    
- Falta de dinamismo,
    
- Dificuldade de escalar para grandes redes com múltiplas organizações.
    

---

## 🧭 Modelo de Confiança no OpenID Federation

No OpenID Federation, a confiança é **hierárquica e delegável**, mas com potencial de **distribuição**.  
A relação inicial de confiança se estabelece da seguinte forma:

plaintext

CopiarEditar

`[ PI ] ─── confia ───> [ Trust Anchor ] <─── confia ─── [ PS ]`

- O **Trust Anchor** é o ponto de referência que valida quem são os participantes confiáveis.
    
- O PI e o PS confiam **no mesmo Trust Anchor**, o que permite estabelecer uma relação indireta de confiança.
    

---

### 🔁 Evolução com Intermediários

Para tornar o sistema **ainda mais flexível**, o modelo permite a introdução de **intermediários**, que atuam como **delegadores de confiança**:

[ PI ] ───> [ Trust Anchor ] <─── [ Intermediário ] <─── [ PS ]

- O **intermediário** é uma entidade que **recebe confiança do Trust Anchor** e pode repassá-la para outros participantes.
    
- Isso facilita o crescimento da federação sem sobrecarregar o Trust Anchor com todas as decisões diretas.
    

---

## 🍃 Entidades Folha no Sistema

As entidades que atuam nas pontas da federação são chamadas de **folhas** e incluem:

### 🔑 OP – _OpenID Provider_

- Equivalente ao **Provedor de Identidade (PI)**.
    
- Responsável por autenticar o usuário e emitir os tokens (`id_token`, `access_token`).
    
- Atua conforme o protocolo OpenID Connect.
    

### 🧾 RP – _Relying Party_

- Equivalente ao **Provedor de Serviço (PS)**.
    
- É quem **inicia o fluxo**, solicitando autenticação e consumindo os tokens.
    
- Confia na identidade emitida pelo OP.
    

### 📦 RS – _Resource Server_

- Servidor que **fornece o recurso protegido** (ex: API).
    
- **Valida os tokens** recebidos da RP, e decide se libera ou não o acesso ao recurso.
    

---

## 🧱 Trust Anchor

- É a **base da confiança da federação**.
    
- Armazena e distribui **metadados assinados digitalmente** que descrevem os participantes confiáveis da rede.
    
- Pode ser uma entidade governamental, consórcio educacional, organização privada, etc.

[[🧠 OpenID Connect (OIDC)]]
[[🌍 Evolução para o Modelo Federado]]

#ProtocoloFederado 