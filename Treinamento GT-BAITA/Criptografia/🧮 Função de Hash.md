
Uma **função de hash** transforma uma mensagem de tamanho arbitrário (**N bits**) em um **valor fixo**, geralmente muito menor (ex: 256 bits).

### 🎯 Objetivo:

Reduzir qualquer mensagem grande a uma **representação compacta**, permitindo:

- Identificação única (quase sempre);
    
- Verificação de integridade;
    
- Otimização de comparações e assinaturas digitais.
    

---

### 🧩 **Representação Conceitual**

|Conjunto A (mensagens)|→|Função de Hash|→|Conjunto B (hashes)|
|---|---|---|---|---|
|Tamanho N (qualquer)||→||Tamanho fixo (ex: 256 bits)|

- **Conjunto A**: contém todas as mensagens possíveis, com infinitas combinações.
    
- **Conjunto B**: espaço reduzido e finito, definido pelas capacidades da máquina (ex: 2²⁵⁶ valores possíveis).
    

---

### ⚠️ **Colisões**

Como o conjunto A é maior que o B, **duas mensagens diferentes podem gerar o mesmo hash** — isso é chamado de **colisão**.

> 🔐 Apesar disso, boas funções de hash tornam a colisão extremamente difícil de acontecer.

---

### 🔍 **Aplicações Práticas**

- **Assinatura digital**  
    Em vez de assinar o documento inteiro, assina-se o **hash** do documento. Isso reduz o custo computacional e mantém a integridade.
    
- **Verificação de integridade**  
    Aplicando o hash em um arquivo antes e depois de uma transmissão ou manipulação, podemos verificar se ele foi **alterado**.
    

---

### ✅ Propriedades Desejáveis de uma Função de Hash

- **Determinística**: mesma entrada gera sempre o mesmo hash.
    
- **Rápida**: deve ser computacionalmente eficiente.
    
- **Resistente a colisões**: difícil encontrar duas entradas com o mesmo hash.
    
- **Resistente à inversão**: não deve ser possível obter a entrada original a partir do hash.

--- 
#Criptografia