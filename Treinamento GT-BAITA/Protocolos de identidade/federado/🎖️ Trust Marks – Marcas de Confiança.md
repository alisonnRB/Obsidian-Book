**Trust Marks** são marcas digitais que indicam que uma entidade cumpre determinadas regras, políticas ou certificações exigidas por uma federação. Elas funcionam como "selos de confiabilidade", sinalizando que uma entidade é reconhecida dentro da federação por estar em conformidade com critérios estabelecidos.

### ✳️ O que são

- São representadas como **JWTs** (JSON Web Tokens).
    
- **Não são obrigatórias**, conforme a especificação — são consideradas uma **extensão opcional** que comunica conformidade.
    
- Quando utilizadas, aparecem no **claim `trust_marks`** do documento da entidade.
    

---

### 🏛️ Participantes do processo

- **TM Issuers (Emissores de Trust Marks):**  
    Entidades autorizadas a emitir trust marks.
    
- **TM Owners (Proprietários de Trust Marks):**  
    Entidades responsáveis por definir as **regras e critérios** para cada tipo de trust mark. Elas **delegam** aos TM Issuers a tarefa de emitir as marcas.
    
- **Trust Anchor:**  
    Entidade central da federação que mantém uma lista de emissores de trust marks compatíveis em um campo chamado **`trust_mark_issuers`**.  
    Essa lista é usada para validar a confiabilidade dos trust marks presentes nos participantes da federação.
    

---

### 📄 Exemplo de estrutura de metadado com trust mark issuers:

	{
	  ...
	  "trust_mark_issuers": [
	    {
	      "tm_type": "https://federation.org/standards/compliance",
	      "tm_issuer": "https://trustmark-issuer.federation.org"
	    }
	  ]
	}

---

### ✅ Verificação de confiança

Quando uma entidade declara possuir um trust mark, ele deve ser:

1. **Assinado** por um emissor listado em `trust_mark_issuers` da Trust Anchor.
    
2. **Verificável** por meio da chave pública do emissor.
    
3. **Condizente com o tipo (`tm_type`)** aceito pela federação.
    

Se todas essas condições forem atendidas, o trust mark é considerado confiável.

Existe uma rota que deve ser implementada, chamada de trust_mark_status, ela permite fazer uma requisição que lista as entidades issuer de marks confiaveis

---

### 📌 Claims típicos de um trust mark (exemplos):

	{
	  "iss": "https://trustmark-issuer.federation.org",
	  "sub": "https://participant.federation.org",
	  "iat": 1710000000,
	  "exp": 1730000000,
	  "tm_type": "https://federation.org/standards/compliance"
	}

---

[[🔎 Resolução de Confiança e Política no OpenID Federation]]
[[🔐 Estrutura de Confiança no OpenID Federation]]


#ProtocoloFederado
