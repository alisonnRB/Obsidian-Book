
O **SAML (Security Assertion Markup Language)** é um protocolo amplamente utilizado em modelos de identidade **centralizados e federados**, permitindo que **serviços (PS)** aceitem autenticação de **provedores de identidade (PI)** de forma segura e padronizada.

---

### 🔗 Funcionamento básico no modelo centralizado

No uso tradicional (centralizado), o SAML opera por meio de **arquivos XML** contendo **metadados** que descrevem:

- Quais **PIs** são confiáveis por um determinado **PS**.
    
- Quais **PSs** são confiáveis por um determinado **PI**.
    
- Inclui **chaves públicas** para **verificação de assinaturas** e **comunicação segura**.

PS ⇄ PI
 ↳ troca de metadados XML com informações como:
     - endpoints
     - certificados (chave pública)
     - formatos suportados

---

### ⚠️ Problemas do modelo tradicional com SAML

- 🔧 **Configuração distribuída e manual**  
    Cada novo serviço precisa trocar e armazenar manualmente os metadados XML.
    
- 🌐 **Escalabilidade limitada**  
    À medida que mais PIs e PSs entram no sistema, o número de relações de confiança **cresce exponencialmente**.
    
- 🔐 **Gestão de chaves espalhada**  
    Certificados públicos ficam distribuídos em diversos ambientes, o que aumenta a complexidade de manutenção.
    

---

## 🌐 SAML no Modelo Federado

Para superar essas limitações, o SAML pode ser utilizado **dentro de uma federação de identidade**, onde:

> Existe uma **entidade central confiável** que mantém e distribui os metadados de **todos os participantes da federação** (PIs e PSs).

### ✅ Vantagens da abordagem federada:

- 🔄 **Atualização centralizada de metadados**  
    Um novo PS ou PI precisa apenas registrar-se na **entidade federativa**.
    
- 🧩 **Escalabilidade**  
    Participantes se conectam indiretamente por meio da autoridade central, evitando múltiplas configurações ponto a ponto.
    
- 🔐 **Gestão de confiança facilitada**  
    A federação distribui os certificados, endpoints e configurações de maneira padronizada e segura.

          [Federação]
               ↑
  ┌───────────────────────┐
  ↓                                                         ↓
[PI A]                                                    [PS B]
   ↓                                                           ↑
Autentica o usuário        Confia no PI via metadados da federação


---

## ❗ Problema na Centralização de SAML em Federações

Embora o uso de **SAML com uma entidade federativa central** traga benefícios como escalabilidade e organização, ele ainda **sofre com limitações importantes**, especialmente em termos de **gestão e evolução da federação**.

---

### 🧱 **Problema Central: Gestão Manual e Burocrática**

A **configuração de novos serviços** (PSs ou PIs), ou a **atualização de participantes já existentes**, é feita por meio de:

- Troca manual de **arquivos XML de metadados**;
    
- Atualização de **certificados e endpoints** manualmente;
    
- Processos **operacionais demorados**, sujeitos a:
    
    - Erros humanos;
        
    - Inconsistências;
        
    - Atrasos burocráticos.
        

---

### 🔁 **Consequência**

A **entidade central da federação** se torna um **gargalo operacional**, pois:

- Precisa validar, aprovar e integrar **manualmente cada novo membro**;
    
- Assumir a responsabilidade de garantir que todos os dados estejam atualizados;
    
- Torna-se um **ponto único de lentidão** e potencial falha.

---

[[🌍 Evolução para o Modelo Federado]]

#Protocolo 