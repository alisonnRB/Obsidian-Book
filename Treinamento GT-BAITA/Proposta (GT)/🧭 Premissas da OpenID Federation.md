
A nova proposta de federação de identidade baseada em OpenID Federation nasce com um conjunto de **premissas fundamentais**, voltadas à escalabilidade, interoperabilidade e facilidade de adoção. São elas:

---

### 🔽 1. Redução de Atrito

- A entrada de **novos participantes** na federação deve ser **rápida, simples e automática**, sem depender de especialistas técnicos como exigido no modelo SAML.
    
- Elimina-se a necessidade de **infraestrutura manual e estática** (ex.: metadados XML configurados à mão).
    
- Reduz-se o **desconforto ou desconfiança do usuário final**, que pode se sentir inseguro ao acessar novos serviços.
    

---

### 🔄 2. Compatibilidade

- É necessário garantir que a nova arquitetura **permita integração com outras instâncias federadas**, como a **eduGAIN** (federação global de identidades acadêmicas).
    
- O sistema deve estar preparado para atuar **em paralelo a estruturas existentes**, mantendo a compatibilidade cruzada.
    

---

### 🌐 3. Interoperabilidade

- A nova federação deve ser capaz de se **comunicar com múltiplas tecnologias e protocolos**, garantindo operação dentro de um ecossistema heterogêneo.
    
- Suporte a diferentes **modelos de trust chain**, políticas de metadados e formatos de tokens.
    

---

### 🏛️ 4. Suporte ao Legado

- A infraestrutura da OpenID Federation deve **conviver com o ecossistema SAML atual**, permitindo que ambos coexistam durante a transição.
    
- A migração deve ser **gradual, sem rupturas**, respeitando o tempo de adaptação das instituições.
    

---

### 👤 5. Experiência do Usuário

- Atualmente, a **CAFe (Comunidade Acadêmica Federada)** não apresenta ao usuário final informações claras sobre sua interação com a federação.
    
- A nova abordagem deve considerar **transparência e usabilidade**, permitindo que o usuário compreenda melhor os fluxos de autenticação e confiança.
    

---

### ⚙️ 6. Facilidade Operacional

- O operador da federação (ex.: **RNP**) deve ser capaz de executar tarefas administrativas com **agilidade e simplicidade**, mesmo em cenários com múltiplos OPs e PSs.
    
- Reduz-se a carga de manutenção e necessidade de suporte técnico intenso.
    

---

### 🔐 7. Controle de Acesso

- Hoje, a **CAFe** **não possui mecanismos de escopo ou privacidade**, tornando todos os serviços automaticamente visíveis e acessíveis à federação.
    
- A nova federação prevê a criação de **escopos de visibilidade e controle de acesso**, possibilitando:
    
    - Serviços públicos,
        
    - Serviços restritos a grupos,
        
    - Serviços privados (acesso limitado por entidade, função ou escopo).
[[🔄SAML vs OpenID Federation]]

#Proposta 