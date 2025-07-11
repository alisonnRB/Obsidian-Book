Para garantir a **transição suave** entre sistemas antigos (baseados em SAML) e a nova arquitetura federada com **OpenID Connect (OIDC)**, são previstos **três níveis de compatibilidade**, com destaque para o uso do **proxy-SATOSA**.

---

### 🔹 **Nível 1: Coexistência Paralela**

- O ecossistema da federação manterá, **simultaneamente**,:
    
    - A **infraestrutura SAML** legada.
        
    - A **nova infraestrutura baseada em OIDC Federation**.
        
- Ambos os modelos funcionam em **paralelo**, permitindo **migração gradual** e sem rupturas.
    

---

### 🔹 **Nível 2: Interoperabilidade entre Federações Paralelas**

Para permitir que serviços OIDC interajam com PIs SAML:

#### 🔁 Introdução do `proxy-SATOSA`

- É um **proxy de tradução entre OIDC e SAML**, escrito em Python.
    
- Ele é **capaz de receber requisições OIDC** e convertê-las em **fluxos SAML**, permitindo interoperabilidade entre dois mundos de autenticação com **semânticas diferentes**.
    

#### 🏗️ Estrutura proposta:

	[ PS OIDC ] → [ Trust Anchor OIDC ] → [ proxy-SATOSA ] → [ PI SAML ]

- O `proxy-SATOSA` atua como **folha (PS)** no XML da federação SAML, mas **repassa a requisição** para o PI real no backend.
    
- Isso **evita a necessidade de reformular o PI SAML** para que ele compreenda OIDC.
    

---

### 🔹 **Nível 3: PS SAML acessando PI OIDC via proxy-SATOSA**

Agora no sentido inverso:

- A proposta também prevê permitir que um **PS SAML** acesse um **PI que opera com OIDC**.
    
- Neste caso, o `proxy-SATOSA` é configurado como **PI no XML** da federação SAML.
    

#### 🧭 Fluxo detalhado:

1. O **PS SAML** faz a requisição de autenticação ao **proxy-SATOSA**, configurado como PI.
    
2. O **proxy-SATOSA** consulta o **WAYF SAML**, que redireciona para ele.
    
3. Ele traduz o fluxo para OIDC e o envia ao **WAYF OIDC**, que redireciona para o **PI OIDC real**.
    
4. Após a autenticação, o **WAYF OIDC** normaliza os atributos.
    
5. Os dados são **reenviados ao proxy-SATOSA**, que os converte de volta para formato SAML.
    
6. Finalmente, o **proxy-SATOSA envia a resposta autenticada ao PS SAML**, mantendo a confiança e integridade.
    

---

### ✅ Benefícios

- **Preserva os investimentos em infraestrutura SAML**.
    
- **Permite que serviços legados continuem operando** com novos provedores OIDC.
    
- **Evita reconstruções complexas** em sistemas antigos.
    
- **Favorece a adoção incremental da OpenID Federation**, sem impacto imediato para os usuários finais.

---

[[🧭 Premissas da OpenID Federation]]
[[🏗️ Arquitetura Proposta]]

#Proposta 


