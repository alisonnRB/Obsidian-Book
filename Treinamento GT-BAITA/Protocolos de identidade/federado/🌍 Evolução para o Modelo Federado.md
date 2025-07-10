Com a ampliação do uso do **modelo centralizado** de **PI (Provedor de Identidade)** e **PS (Provedor de Serviço)**, surgem **novos desafios**, especialmente em **ambientes grandes e heterogêneos**, como universidades e organizações públicas.

### ⚠️ Problemas do Modelo Centralizado em Larga Escala

- Cada organização (ex: universidade) centraliza todos os seus serviços (PSs) sob seu **próprio PI**.
    
- Isso cria **diversos "feudos" de identidade**, onde usuários só conseguem acessar serviços **da própria instituição**.
    
- Impossibilita ou dificulta o **acesso a serviços de outras organizações**, mesmo que sejam confiáveis.

### 🤝 Solução: **Modelo Federado**

O **modelo federado** surge como uma **evolução natural**, permitindo que:

> Um **usuário autenticado por um PI externo** possa acessar **serviços (PSs)** que pertencem a uma organização diferente.

---
## 🔐 Como Confiar em PIs Externos?

Em um **modelo federado**, cada **Provedor de Serviço (PS)** precisa **confiar** nos **Provedores de Identidade (PIs)** que autenticarão usuários em seu nome. Mas como essa confiança é estabelecida e mantida?

---

### 🧩 Solução: Lista de PIs Confiáveis

Cada PS mantém uma **lista de PIs confiáveis**, ou seja, **fontes autorizadas de identidade**.  
Esses PIs precisam atender a critérios técnicos e de segurança.

---

### ❓ Como tornar isso viável (e escalável)?

Estabelecer e manter relações de confiança manualmente entre todos os PSs e PIs seria **inviável em larga escala**. A solução está em **protocolos e estruturas padronizadas**, como:

[[🧾 PS e PI — Conceitos Fundamentais]]

#ProtocoloFederado