
- **PS (Provedor de Serviço):**  
    Sistema responsável por fornecer um serviço ou funcionalidade específica ao usuário (ex: plataforma de e-mail, sistema de gestão, app de mensagens, etc.).
    
- **PI (Provedor de Identidade):**  
    Sistema centralizado que gerencia identidades digitais, realizando autenticação e controle de acesso (ex: Keycloak, Google, Facebook Login).
    

---

## 🧱 Modelo Isolado

Antigamente, era comum que cada **serviço (PS)** fosse também responsável por gerenciar suas **próprias identidades (PI)**.

### ⚠️ Problemas:

- Repetição de gerenciamento de credenciais.
    
- Maior complexidade para os desenvolvedores.
    
- Usuário precisava lembrar várias senhas.
    
- Múltiplos logins para diferentes serviços.
    

### 🔧 Estrutura:

          [Banco de Dados]                         [Banco de Dados]
                 ↑                                       ↑
             credenciais                             credenciais
                 ↑                                       ↑
         ┌─────────────┐                           ┌─────────────┐
         │ Serviço 1   │ ← PS + PI                 │ Serviço 2   │ ← PS + PI
         └─────────────┘                           └─────────────┘
                ↑                                       ↑
                |                                       |
             [Usuário]                                [Usuário]


---

## 🌐 Modelo Centralizado

Neste modelo moderno, a **autenticação** é separada do serviço. O PI centraliza o controle de identidade, enquanto os PSs apenas delegam essa responsabilidade.

### ✅ Benefícios:

- O usuário utiliza uma única identidade para múltiplos serviços.
    
- Menor carga de segurança para os PSs.
    
- Facilidade de login e acesso unificado.
    

### ⚠️ Desafio:

- Os PSs devem **confiar** na legitimidade e segurança do PI.
    

### 🔧 Estrutura:

         [Banco de Dados - Identidades]
                   ↑
             (credenciais)
                   ↑
             ┌────────┐
             │   PI   │ ← Provedor de Identidade
             └────────┘
                 ↑
         ┌───────┴────────┐
         ↓                ↓
 ┌─────────────┐   ┌─────────────┐
 │        Serviço 1          │   │         Serviço 2         │  ← PSs
 └─────────────┘   └─────────────┘
         ↑                                                ↑
         └──────[Usuário] ───────┘


[[🌍 Evolução para o Modelo Federado]]
#Protocolo