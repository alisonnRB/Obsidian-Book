
O OpenID Federation define a **confiança entre entidades** por meio de documentos assinados, organizados em dois tipos principais:

---

### 🧾 1. **Entity Configuration** (Autoafirmação)

Cada entidade participante da federação (como um OP, RP, Intermediário ou Trust Anchor) possui um **`Entity ID`**, que geralmente é representado como uma **URL baseada em domínio**.

Essa entidade gera um documento chamado **Entity Configuration**, que é:

- Uma **autoafirmação assinada digitalmente**;
    
- Contém sua **chave pública**, metadados, capacidades e informações técnicas;
    
- Serve como ponto inicial para **descoberta e verificação** da identidade da entidade.
    

> A presença do campo `iss` (issuer) no JSON indica que o documento é uma **Entity Configuration**.

---

### 📜 2. **Trust Statements (Subordinate Statements)**

São **declarações de confiança assinadas** por uma entidade superior sobre uma entidade subordinada.

Ou seja:

> Uma entidade assina um **documento declarando a confiabilidade de outra entidade abaixo dela** na hierarquia federada.

Essas declarações:

- São conhecidas como **Subordinate Statements**;
    
- Contêm o campo `sub` que indica **quem está sendo descrito**;
    
- São **assinadas pela entidade superior**, que aparece como `iss`;
    
- Podem ser emitidas por **Trust Anchors** ou **Intermediários**;
    
- Têm o papel de **delegar confiança** e **compor a cadeia de validação**.
    

---

### 🏗️ Cadeia de Validação

A confiança é validada através da **cadeia de documentos** que ligam:

	Entidade Folha (RP ou OP)
	   ↓
	Intermediário (opcional)
	   ↓
	Trust Anchor

Cada etapa da cadeia:

- Contém assinaturas válidas;
    
- Tem o `Entity ID` conhecido e registrado;
    
- Define os **endpoints e escopos de autoridade** da entidade abaixo.


[[🌐 OpenID Federation – Confiança Distribuída]]
[[🔐 JWS – JSON Web Signature]]

#ProtocoloFederado 