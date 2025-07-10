
### ✅ **Criptografia Simétrica**

Utiliza **uma única chave** para cifrar e decifrar a mensagem.

`mensagem       →   | Cifragem  |   →   código   →   | Decifragem |   →   mensagem                  (chave X)                          (chave X)`

- ✔️ Vantagem: mais rápida em comparação com criptografia assimétrica.
    
- ⚠️ Problema: exige **acordo prévio entre as partes** para compartilhamento da mesma chave de forma segura.
    

---

### 🔑 **Criptografia Assimétrica**

Cada participante possui um **par de chaves**:

- **Chave pública:** pode ser compartilhada com qualquer um.
    
- **Chave privada:** deve ser mantida em segredo.
    

Essas chaves são matematicamente relacionadas, permitindo que:

- O que for **cifrado com a chave pública**, só possa ser **decifrado com a chave privada** correspondente, e vice-versa.


`mensagem       →   | Cifragem  |   →   código   →   | Decifragem |   →   mensagem               (chave pública)                    (chave privada)`

#### 📝 Exemplo prático:

- Alguém quer enviar uma mensagem para você com sigilo. Essa pessoa usa **sua chave pública** para cifrar a mensagem.
    
- Só você, com **sua chave privada**, poderá decifrá-la.
    

---

### 🚫 **Limitação da Criptografia**

Mesmo garantindo **confidencialidade**, a criptografia **não garante:**

- **Integridade:** a mensagem pode ter sido alterada no caminho;
    
- **Autenticidade e autoria:** precisamos de mecanismos que comprovem **quem enviou a mensagem** (não repúdio).
    

➡️ Para isso, usamos **assinaturas digitais** (abordadas em tópicos seguintes).

[[🔐 JWS – JSON Web Signature]]

--- 

#Criptografia