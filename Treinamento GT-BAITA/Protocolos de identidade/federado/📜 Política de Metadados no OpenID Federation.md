No OpenID Federation, as **políticas de metadados** são definidas e aplicadas de forma **hierárquica**, respeitando a estrutura da **trust chain**.

---


## 🧾 Estrutura da `metadata_policy` no OpenID Federation

A política de metadados (`metadata_policy`) define **restrições e regras obrigatórias** para os metadados de uma entidade.  
Ela é aplicada por entidades superiores na **trust chain**, como Intermediários ou Trust Anchors.

---

### 🧬 Estrutura geral

	"metadata_policy": {
	  "<tipo_de_entidade>": {
	    "<campo>": <valor_ou_regra>,
	    ...
	  }
	}

---

### 🧭 Como funciona?

Cada entidade superior na cadeia (ex: Trust Anchor ou Intermediário) define uma **política de metadados** que os participantes subordinados **devem seguir obrigatoriamente**.

Essas políticas determinam:

- Quais campos devem estar presentes nos metadados;
    
- Quais valores são aceitos ou obrigatórios;
    
- Restrições sobre o comportamento das entidades (ex: métodos de autenticação, escopos suportados);
    
- Limitações sobre entidades confiáveis e profundidade da cadeia (`max_path_length`).
    

---

### 🔒 Propósito da política

A política de metadados:

- **Garante a consistência** entre as entidades participantes;
    
- **Estabelece as regras de confiança** da federação;
    
- **Permite controle descentralizado** (quando intermediários aplicam políticas regionais ou específicas);
    
- **Impede que entidades mal configuradas ou maliciosas** participem da federação.
    

---

### 🧬 Aplicação na cadeia de confiança

Em termos práticos:

- O **Trust Anchor** publica uma política com seus critérios.
    
- O **Intermediário**, ao confiar no Trust Anchor, deve seguir essa política.
    
- Ao mesmo tempo, o Intermediário **pode impor políticas próprias** para os participantes que confiam nele.
    
- Essas políticas podem ser incluídas diretamente nas **Subordinate Statements**, sobrescrevendo ou restringindo os metadados das entidades subordinadas.
    

---

### 🏛️ Resumo

> A **política de metadados** define os **limites e obrigações contratuais** das entidades dentro da federação.

Ela atua como o **marco normativo técnico** da confiança federada.

---

[[🗂️ Metadata no OpenID Federation]]
[[🔗 Trust Chain (Cadeia de Confiança)]]

#ProtocoloFederado 