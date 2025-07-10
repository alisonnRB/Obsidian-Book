
A **Trust Chain** é a cadeia de assinaturas digitais que permite **verificar a confiabilidade de uma entidade** por meio de um encadeamento de documentos assinados até alcançar a **Trust Anchor**.

[ EC ] → [ SS ] → [ Intermediário SS ] → [ Trust Anchor ]

Legenda:

- **EC** = Entity Configuration (autoafirmação da entidade)
    
- **SS** = Subordinate Statement (declaração assinada por um nível acima)
    
- **TA** = Trust Anchor (autoridade máxima da confiança)

### 🔐 Funcionamento passo a passo:

1. **EC (Entidade Folha)**
    
    - A entidade (ex: RP) gera sua **Entity Configuration** e a assina com sua **chave privada**.
        
    - Documento contém metadados e sua própria `public_key`.
        
2. **Intermediário gera SS**
    
    - Recebe a EC da entidade folha.
        
    - **Verifica** a assinatura usando a `public_key` da EC.
        
    - Se válida, emite um **Subordinate Statement** declarando confiança nesta entidade.
        
    - Esse SS é então **assinado com a chave privada do intermediário**.
        
3. **Trust Anchor gera novo SS**
    
    - O Trust Anchor recebe o SS do intermediário.
        
    - Verifica a assinatura.
        
    - Emite sua própria **declaração de confiança sobre o intermediário**.
        
    - Essa assinatura fecha a cadeia.
        
4. O cliente (ex: outro RP ou um OP) pode **verificar a cadeia inteira**, confirmando que:
    
    - Cada assinatura é válida;
        
    - A autoridade vem de um **Trust Anchor conhecido e confiável**.
        

---

### 🧪 Representação com identidades:

[ RP ]
 └─ EC (assinado pelo RP)

[ Intermediário ]
 └─ SS (sobre o RP, assinado pelo Intermediário)

[ Trust Anchor ]
 └─ SS (sobre o Intermediário, assinado pela TA)
 
---

### ✅ Resultado

Se a **cadeia de assinaturas for válida**, qualquer outra entidade (como um OP ou outro RP) pode confiar que:

- O RP é legítimo;
    
- Está sob um intermediário autorizado;
    
- E esse intermediário foi delegado por uma **Trust Anchor confiável**.


---

[[🔐 Estrutura de Confiança no OpenID Federation]]

#ProtocoloFederado 