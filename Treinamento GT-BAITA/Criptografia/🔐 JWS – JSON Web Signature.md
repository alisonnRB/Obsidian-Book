

O **JWS** é um padrão usado para representar **dados assinados digitalmente** em formato JSON. Ele garante **integridade** e **autenticidade** da informação por meio de assinatura digital.

Existem **dois formatos** principais de serialização:

---

### 1️⃣ **Compact Serialization**

Formato compacto, amplamente usado em **transmissão via HTTP (ex: Authorization Header)**.

`BASE64URL(header) . BASE64URL(payload) . BASE64URL(signature)`

#### 🔹 Exemplo de estrutura:


`eyJhbGciOiJSUzI1NiIsInR5cCI6IkpXVCJ9 . eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkFsaXNvbiIsImlhdCI6MTUxNjIzOTAyMn0 . c2lnbmF0dXJhRGVjcnlwdGFkYUNvbUNoYXZlUHZ`

#### 📌 Observações:

- Os três segmentos são separados por **pontos (`.`)**.
    
- O **header** e o **payload** são os **dados visíveis**.
    
- A **assinatura** é aplicada sobre os dois primeiros campos combinados.
    

---

### 2️⃣ **JSON Serialization**

Formato mais **estruturado** e **legível**, ideal para APIs que lidam com múltiplas assinaturas ou para leitura humana.

json

CopiarEditar

`{   "payload": "<dados base64url>",   "protected": {     "alg": "RS256",     "typ": "JWT"   },   "header": {     "kid": "chave-123"   },   "signature": "<assinatura base64url>" }`

#### 📌 Observações:

- O campo `"protected"` é **incluso na assinatura**, garantindo que não possa ser alterado sem invalidá-la.
    
- O campo `"header"` (não protegido) pode conter metadados adicionais.
    

---

### 🆚 **Resumo: Compact vs JSON**

|Característica|Compact Serialization|JSON Serialization|
|---|---|---|
|Leitura humana|Menos legível|Mais legível|
|Tamanho|Mais compacto|Maior (estruturado)|
|Uso comum|Headers HTTP, tokens JWT|APIs com múltiplas assinaturas|
|Proteção do header|Header é sempre protegido|Apenas o campo `"protected"`|

[[✍️ Assinatura Digital com RSA e Hash]]
[[🧮 Função de Hash]]

--- 
#Criptografia