Nos modelos centralizados tradicionais, a confiança era depositada em **um único órgão**, responsável por **registrar manualmente** os provedores (OPs e PSs).  
Esse processo era lento, burocrático e propenso a erros.

Com o modelo federado, é possível **automatizar o registro** de provedores durante o próprio fluxo de autenticação, desde que exista uma **cadeia de confiança (trust chain)** válida.

---

### 🔁 Exemplo prático

Um **OP (OpenID Provider)** nunca recebeu uma requisição de autenticação de um determinado **PS (Relying Party)**.

Ao receber uma requisição **pela primeira vez**, o OP pode:

1. **Validar a confiança** do PS através da **trust chain** fornecida na requisição.
    
2. **Registrar automaticamente** esse PS se a confiança for estabelecida.
    
3. **Autenticar** o serviço, sem necessidade de pré-cadastro manual.
    

---

### 🔐 Etapas do processo

1. **Verificação de Registro**
    
    - Se o PS **não está registrado**, o OP **remonta a trust chain** até a Trust Anchor para **avaliar a legitimidade**.
        
    - Se o PS **já estiver registrado**, o OP usa a nova trust chain recebida na requisição para **atualizar o caminho de confiança**.
        
2. **Verificação de Metadados**
    
    - Os metadados fornecidos pelo PS na trust chain devem ser **validados** segundo as políticas estabelecidas (ex.: estrutura, assinatura, escopos, timestamps).
        
3. **Estabelecimento de Confiança**
    
    - Se toda a trust chain for válida e os metadados estiverem de acordo, o OP **estabelece a confiança** com o PS.
        
4. **Registro e Continuação**
    
    - O PS pode ser **automaticamente registrado** no OP, e a requisição de autenticação segue normalmente.
        

---

✅ Essa abordagem torna o ecossistema federado **mais dinâmico**, **menos burocrático** e **mais escalável**, especialmente em ambientes com múltiplas organizações e entidades envolvidas.

---

[[🔎 Resolução de Confiança e Política no OpenID Federation]]
[[🔗 Trust Chain (Cadeia de Confiança)]]
[[📜 Política de Metadados no OpenID Federation]]

#ProtocoloFederado 