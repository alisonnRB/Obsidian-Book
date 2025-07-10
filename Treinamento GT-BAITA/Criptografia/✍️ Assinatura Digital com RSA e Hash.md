
Para garantir **autenticidade**, **integridade** e **não repúdio** em documentos que podem passar por múltiplos acessos, utilizamos uma combinação de **função de hash** e **criptografia assimétrica (RSA)**.

---

### 🔐 **Fluxo do Processo**

     Documento
         ↓
     Hash H(d)
         ↓
┌──────────────────────────────┐
│ Cifrado com chave privada   │  ← RSA
└──────────────────────────────┘
         ↓
   Assinatura Digital
         ↓
 ( Envio do Documento + Assinatura + Chave Pública )
         ↓
┌──────────────────────────────┐
│ Verificação com chave pública│ ← RSA
└──────────────────────────────┘
         ↓
    Hash decifrado (H(d))
         ↓
    Comparação com novo hash H'(d)
         ↓
    Resultado: ✅ True / ❌ False


---

### 🧭 **Passo a Passo**

1. **Hash do documento**  
    O documento é compactado com uma **função de hash** → gera `H(d)`.
    
2. **Assinatura com RSA (chave privada)**  
    O hash é cifrado com a **chave privada** do autor, gerando a **assinatura digital**.
    
3. **Envio do documento**  
    O documento é enviado junto com a **assinatura** e a **chave pública** do autor.
    
4. **Verificação**  
    O destinatário:
    
    - Aplica a mesma função de hash ao documento recebido → `H'(d)`
        
    - Decifra a assinatura com a **chave pública** do autor → obtém `H(d)`
        
    - Compara `H(d)` com `H'(d)`
        
    - Se forem iguais, a mensagem **não foi alterada** e o autor é **autenticado**.
        

---

### 🧠 **Por que funciona?**

- **Autenticidade**: só o detentor da chave privada poderia gerar aquela assinatura.
    
- **Integridade**: qualquer alteração no documento muda o hash → assinatura inválida.
    
- **Não repúdio**: o autor não pode negar que assinou, pois só ele possui a chave privada.
    

---

### 🧮 Sobre o RSA

O **RSA** é um algoritmo de criptografia assimétrica baseado em:

- **Aritmética modular**
    
- **Fatoração de grandes números primos**
    

> A segurança do RSA está na **dificuldade computacional** de fatorar o produto de dois números primos grandes. Essa operação é **viável para gerar** as chaves, mas **inviável para quebrar** a criptografia com os recursos atuais.


[[🧮 Função de Hash]]

--- 

#Criptografia