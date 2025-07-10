**Shibboleth** é uma **implementação open-source do protocolo SAML**, amplamente utilizada em **federações de identidade**, especialmente no contexto **acadêmico** (ex: universidades, bibliotecas digitais, repositórios de pesquisa).

---

### 🧱 Componentes Principais no Shibboleth

Shibboleth define e opera com os seguintes papéis:

- **PI (Provedor de Identidade)**  
    Responsável por autenticar o usuário (ex: universidade do aluno).
    
- **PS (Provedor de Serviço)**  
    Fornece acesso a um recurso (ex: portal de artigos acadêmicos).
    
- **WAYF (Where Are You From?)**  
    Também chamado de **Discovery Service** (serviço de descoberta).  
    Permite que o **usuário escolha seu PI**, quando o PS **não sabe de onde ele vem**.
    

---

### 🔄 Fluxo de Autenticação com Shibboleth + WAYF

1. Usuário tenta acessar um recurso no PS.
2. O PS não sabe qual é o PI do usuário.
3. O PS redireciona o navegador do usuário para o WAYF.
4. O WAYF apresenta uma lista de PIs confiáveis (com base nos metadados SAML).
5. O usuário seleciona seu PI.
6. O navegador é redirecionado para o PI escolhido.
7. O PI autentica o usuário.
8. O PI gera uma asserção SAML e redireciona o usuário de volta ao PS.
9. O PS valida a asserção (verifica a assinatura) e libera o acesso.

---

### 📄 Metadados e Confiança

O WAYF, o PS e os PIs **compartilham metadados XML** definidos pela federação, contendo:

- Lista de participantes;
    
- URLs de endpoints;
    
- Certificados (chaves públicas) para validação das assinaturas.
    

---

### ⚠️ Observação importante

- O **WAYF não autentica ninguém**. Ele **apenas auxilia** o PS a **descobrir o PI** do usuário.
    
- O **termo moderno para WAYF é "Discovery Service"**, já que o nome original caiu em desuso por ser considerado pouco inclusivo.


[[📄 SAML em Ambientes Federados]]

#Protocolo 