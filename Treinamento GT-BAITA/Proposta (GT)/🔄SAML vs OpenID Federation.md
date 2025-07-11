
|Aspecto|🧾 **SAML (Legado)**|🔐 **OpenID Federation**|
|---|---|---|
|**Modelo de Confiança**|Centralizado|Descentralizado / Distribuído|
|**Papel de Integração**|Manual (via arquivos XML entre entidades)|Automático e dinâmico (via trust chain)|
|**Formato de Configuração**|XML|JSON + JWT|
|**Descoberta de Entidades**|Manual (pré-registro)|Dinâmica (com discovery e metadata endpoint)|
|**Gerenciamento de Chaves**|Estático, configurado por arquivo|Dinâmico, via metadata assinado|
|**Extensibilidade**|Limitada|Modular (extensões como Trust Marks, Metadata Policy, etc)|
|**Padronização Moderna**|Descontinuado|Ativamente desenvolvido pelo OpenID Foundation|
|**Escalabilidade**|Baixa (dificuldade de gerenciar muitas entidades)|Alta (resolução automática e políticas hierárquicas)|
|**Exemplo de Ferramenta**|Shibboleth|OpenID Federation Draft + Implementações futuras|
|**Objetivo Atual**|Legado, manutenção de compatibilidade|Pensado para o presente e futuro da identidade digital|

---

### ✅ Resumo

- **SAML** foi essencial para padronizar federações de identidade no passado, mas tornou-se **engessado e difícil de escalar**.
    
- **OpenID Federation** nasce para resolver esses problemas com um modelo **modular, automatizado e interoperável**, facilitando a adoção e integração entre múltiplos provedores.

[[🌐 OpenID Federation – Confiança Distribuída]]
[[📄 SAML em Ambientes Federados]]


#Proposta