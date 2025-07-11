O **WAYF** é uma entidade intermediária essencial em federações de identidade, cuja função é **resolver a origem do usuário** ao acessar um serviço federado.

---

### 🎯 Motivação

No contexto atual da **CAFe**, faltam mecanismos para lidar com:

- Múltiplos **fatores de autenticação**.
    
- **Descoberta de Provedores de Identidade (PIs)** de forma padronizada e integrada.
    

Isso dificulta:

- A escalabilidade da federação.
    
- A experiência do usuário.
    
- A adoção de autenticações mais robustas.
    

---

### 🔧 Função do WAYF na nova arquitetura federada

- Serve como **intermediário entre o usuário e o Provedor de Serviço (PS)**.
    
- Ao acessar um serviço, o usuário é **redirecionado para o WAYF**, que:
    
    - **Lista os Provedores de Identidade (PIs)** registrados na **Trust Anchor**.
        
    - Permite ao usuário **escolher seu PI** de forma padronizada.
        
    - Redireciona o fluxo para o PI correto, com base na escolha.
        

> 📌 Isso **elimina a necessidade de cada PS implementar sua própria descoberta de PI**, o que seria inviável em larga escala.

---

### 📌 Funções adicionais do WAYF

- **Mapeia os atributos de cada PI**, como escopos, nível de autenticação, mecanismos de MFA (multi-factor authentication), etc.
    
- **Normaliza** e adapta essas características conforme as **regras de interoperabilidade da federação**, garantindo uma experiência consistente.
    

---

### ✅ Benefícios

- Centraliza a **descoberta de identidade**.
    
- Simplifica a **experiência do usuário**.
    
- Garante **escalabilidade** e **interoperabilidade**.
    
- Suporta múltiplos níveis e fatores de autenticação de forma coordenada.



[[🏗️ Arquitetura Proposta]]

#Proposta 