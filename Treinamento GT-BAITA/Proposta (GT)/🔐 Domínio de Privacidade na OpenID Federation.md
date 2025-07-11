A arquitetura federada moderna prevê **níveis distintos de privacidade e controle de visibilidade**, permitindo ajustar o escopo de confiança e a exposição pública das entidades dentro da federação.

Esses níveis formam o conceito de **Domínio de Privacidade**, que organiza como as entidades se relacionam e **quem pode descobrir ou confiar em quem**.

---

### 🔹 **Nível 1 – Federação Pública**

- **Todas as ligações são públicas e abertas**.
    
- Os relacionamentos entre os participantes da federação são **descobertos e visíveis**.
    
- Permite **autenticação cruzada entre qualquer RP e OP**, desde que a trust chain esteja estabelecida.
    
- É o modo padrão da **federação CAFe** e **eduGAIN**.
    

---

### 🔹 **Nível 2 – Âncora Privada (Isolada)**

- Cria-se uma **Trust Anchor privada**, **sem conexão direta com a âncora pública** da federação (ex: CAFe).
    
- A ausência de conexão impede a **descoberta automática** e a **construção da trust chain com entidades externas**.
    
- **Somente os membros abaixo dessa âncora privada** conseguem se autenticar entre si.
    
- Permite criar **grupos isolados** com autenticação interna usando o modelo federado, **sem exposição pública**.
    

> 📌 **Uso comum:** ambientes internos de universidades, setores com regras próprias, testes de integração, ou projetos sob sigilo.

- Cada âncora privada define **suas próprias políticas** de metadados, trust marks e registro de entidades subordinadas.
    

---

### 🔹 **Nível 3 – Escopos Privados dentro da Federação Pública**

- Ao invés de criar uma âncora totalmente isolada, esse nível permite a **criação de escopos restritos dentro da federação pública**.
    
- A âncora principal (ex: CAFe) define **escopos de visibilidade e acesso controlado**, que agrupam entidades específicas.
    
- Esses escopos operam como **zonas privadas**, mas **ainda dentro da federação maior**, possibilitando controle granular de acesso sem perder interoperabilidade.
    

> 📌 Exemplo: permitir que somente instituições de ensino superior públicas compartilhem um grupo privado de autenticação para sistemas específicos.

---

### ✅ Resumo Comparativo

|Nível|Modelo|Visibilidade|Trust Chain Externa|Exemplo de Uso|
|---|---|---|---|---|
|1|Federação Pública|Total|Sim|CAFe, eduGAIN|
|2|Âncora Privada Isolada|Restrita (interna)|Não|Ambientes internos, testes|
|3|Escopo Privado na Federação|Limitada (segmentada)|Sim (controlada)|Agrupamento institucional, sigilo parcial|


---

[[🏗️ Arquitetura Proposta]]

#Proposta 