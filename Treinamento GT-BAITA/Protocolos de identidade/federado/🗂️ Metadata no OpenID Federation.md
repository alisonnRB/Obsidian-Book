Durante a construção da **trust chain**, cada entidade publica metadados que descrevem suas capacidades, endpoints e políticas de operação.

> É possível que **Subordinate Statements sobrescrevam os metadados definidos na Entity Configuration**, para impor restrições ou padronizações de entidades superiores.

---

### 🧬 Estrutura dos metadados

A estrutura segue o formato JSON com base no **tipo da entidade**:

	<tipo_da_entidade>: {
	  "metadata": {
	    <tipo_de_metadata>: {
	      <campo>: <valor>,
	      ...
	    }
	  }
	}

Exemplo (estrutura geral):

	"federation_entity": {
	  "metadata": {
	    "federation_entity": {
	      "organization_name": "Federação Brasileira",
	      "contacts": ["admin@federacao.br"],
	      "federation_fetch_endpoint": "https://fed.br/fetch",
	      "federation_resolve_endpoint": "https://fed.br/resolve",
	      "policy_uri": "https://fed.br/politica"
	    }
	  }
	}

---

## 🏛️ Federation Entity

O tipo `federation_entity` representa uma **entidade gestora de confiança**: Trust Anchor ou Intermediário.

### 🔖 Metadados típicos em `federation_entity`:

|Campo|Descrição|
|---|---|
|`organization_name`|Nome da entidade gestora da federação|
|`contacts`|Contatos administrativos|
|`federation_fetch_endpoint`|Endpoint para buscar documentos de participantes|
|`federation_resolve_endpoint`|Endpoint para resolução da trust chain|
|`policy_uri`|URI das políticas da federação|
|`constraints`|Regras de controle, como número máximo de saltos, entidades permitidas, etc.|

---

🧠 A sobrescrita de metadados por Subordinate Statements permite que o controle **da autoridade superior prevaleça** na cadeia.


[[🌐 OpenID Federation – Confiança Distribuída]]

#ProtocoloFederado 