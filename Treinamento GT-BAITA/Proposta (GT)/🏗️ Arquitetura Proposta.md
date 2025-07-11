A nova arquitetura da federação brasileira (CAFe) prevê integração com a federação global **eduGAIN**, alinhando-se ao modelo de **OpenID Federation** e mantendo interoperabilidade com sistemas legados.

---

### 🧱 1. Trust Anchor Nacional conectada à eduGAIN

- A **Trust Anchor da CAFe** será **conectada à Trust Anchor da eduGAIN**, estabelecendo uma cadeia de confiança internacional.
    
- Para isso, a CAFe precisa obter da eduGAIN uma **Trust Mark internacional**.
    
- Para receber essa Trust Mark, a CAFe **precisa primeiro emitir sua própria Trust Mark nacional**, que **representa sua identidade como federação confiável**.
    

---

### 🔁 2. Introdução do `proxy_oidc_fed`

#### ✳️ Objetivo:

Atuar como **ponte entre sistemas legados ou não compatíveis com OpenID Federation** e o ecossistema federado moderno.

#### 🔧 Comportamento:

|Posição no ecossistema|A quem se apresenta como...|
|---|---|
|Dentro da federação (ex: eduGAIN)|**Um Provedor de Serviço (RP)**|
|Para aplicações legadas|**Um Provedor de Identidade (OP)**|

> Assim, o `proxy_oidc_fed` atua como **tradutor de protocolos** e **ponto de mediação**, permitindo que sistemas sem suporte nativo a OpenID Federation participem da federação sem necessidade de grandes alterações técnicas.

---

### 📄 3. Requisitos do Proxy

- Como será visto como uma **folha (entidade final)** pela federação, o `proxy_oidc_fed` **precisa de uma Entity Configuration (EC)** própria, contendo:
    
    - Seu `entity_id`,
        
    - Chave pública,
        
    - Metadados,
        
    - Possíveis Trust Marks.
        
- O `proxy_oidc_fed` **herda ou negocia a trust chain** da federação para permitir autenticação segura.
    

---

### ✅ Benefícios da Arquitetura

- **Desonera** aplicações legadas da responsabilidade de implementar o novo protocolo.
    
- **Acelera a adoção** da OpenID Federation pela CAFe.
    
- **Garante compatibilidade** com a eduGAIN de forma gradual e escalável.
    
- **Centraliza a tradução e adaptação** dos fluxos OIDC não-federados para o contexto federado.

---

[[🧭 Premissas da OpenID Federation]]

#Proposta 