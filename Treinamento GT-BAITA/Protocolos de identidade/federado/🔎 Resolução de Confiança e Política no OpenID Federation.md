Para aceitar uma requisição federada com segurança, um serviço precisa **avaliar a confiabilidade da entidade que a originou**. Esse processo envolve dois passos fundamentais:

---

## 🔐 1. Resolução de Confiança (Trust Resolution)

Quando uma entidade (ex: um RP) tenta consumir um serviço (ex: OP), o serviço precisa **verificar a identidade e confiabilidade do RP** com base na **trust chain**.

### 📌 Etapas do processo:

1. **Recebimento da requisição**
    
    - O serviço (OP) recebe uma requisição autenticada, normalmente representada por um **JWT**.
        
    - Dentro do JWT, o campo `authority_hints` informa **qual entidade superior assinou** ou é responsável pela confiança do remetente.
        
2. **Descoberta recursiva**
    
    - Com base no `authority_hints`, o serviço faz requisições para os endpoints das entidades, recuperando seus **`Entity Statements`**.
        
    - A cada etapa, ele identifica a entidade superior (`iss`) e continua subindo na hierarquia até alcançar a **Trust Anchor**.
        
3. **Montagem da trust chain**
    
    - A cadeia completa de confiança é composta por:
        
        - `Entity Configuration` (da entidade folha);
            
        - Uma ou mais `Subordinate Statements`;
            
        - O `Entity Statement` final emitido pela Trust Anchor.
            
4. **Verificações realizadas em cada JWT da cadeia**:
    
    - 🔒 Assinatura digital válida (com chave pública da entidade `iss`);
        
    - 📅 Campo `iat` (Issued At): deve estar no passado;
        
    - 🕒 Campo `exp` (Expiration): deve estar no futuro;
        
    - 📘 Tipo correto: `Entity Configuration` ou `Subordinate Statement`;
        
    - 🧭 Correlação entre `iss`, `sub` e `authority_hints`.
        

---

## 📜 2. Resolução de Política (Policy Resolution)

Após montar e validar a trust chain, é necessário verificar se os **metadados da entidade subordinada estão em conformidade com as políticas herdadas** ao longo da cadeia.

### 📌 Etapas do processo:

1. **Coleta das políticas**
    
    - Cada `Subordinate Statement` pode conter uma seção `metadata_policy`, que define regras obrigatórias para os metadados da entidade abaixo.
        
2. **Mesclagem das políticas**
    
    - As políticas de todos os SSs são **combinadas em cascata**, resultando em uma **política final efetiva**.
        
3. **Sobrescrita de metadados**
    
    - Importante: Os `Subordinate Statements` **podem sobrescrever os metadados do `Entity Configuration`** imediatamente abaixo deles.
        
    - Isso significa que **os metadados finais a serem validados não são os originais da EC**, mas os modificados pelas camadas superiores.
        
4. **Comparação com a política final**
    
    - Os metadados finais (pós-sobrescrita) são comparados com a **política mesclada**.
        
    - Se todos os requisitos forem atendidos, a entidade é considerada **confiável e em conformidade com a federação**.
        

---

### ✅ Resultado

A entidade (ex: RP) só é aceita se:

- A **trust chain** for válida em termos de assinatura, tempo e estrutura;
    
- Os **metadados finais** forem **compatíveis com as políticas** definidas pela cadeia.


---


[[🔗 Trust Chain (Cadeia de Confiança)]]
[[🔐 Estrutura de Confiança no OpenID Federation]]
[[🗂️ Metadata no OpenID Federation]]
[[📜 Política de Metadados no OpenID Federation]]

#ProtocoloFederado 