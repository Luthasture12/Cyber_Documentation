# Encryption

Encryption is a process of turning regular text, called **plaintext**, into text that cannot be read by outside parties, called **ciphertext**. It does this through a process known as an **algorithm**. There are several algorithms that can be used. Most of the time, they will use a **key**, which is something that is required to turn plaintext into ciphertext, and vice versa.  
	The process of turning plaintext into ciphertext is called encryption. Ciphertext can get turned into plaintext when it reaches its target. This process is called decryption.

There are several types of encryption:  
	**Symmetric** \- a type of encryption that uses a key to encrypt and decrypt. For symmetric encryption, the same key is used to encrypt and decrypt. The person sending the message will encrypt the message with the key, and then they send the message and key to the target. The target uses the key to decrypt the message. The tricky part in using symmetric encryption is getting the key to the target. If the key is stolen or intercepted, the interceptor can use that key to decrypt and read the messages.

A common algorithm used in symmetric encryption is **AES,** Advanced Encryption Standard. 

	**Asymmetric** \- a type of encryption that uses two keys, one to encrypt and one to decrypt. One key is referred to as the **public key**. This key is given away to people who want to communicate. People can use the public key to encrypt their message, and then they send the message to the recipient, the person who gave out the public key. The recipient then uses the other key, called the **private key**. The private key is only owned by the recipient who generated, or created, the public key. The private key is used to decrypt incoming messages.

	A common algorithm used in asymmetric encryption is **RSA**, Rivest–Shamir–Adleman (named after the three people who came up with this algorithm).

**A NOTE ON QUANTUM COMPUTING AND ENCRYPTION**: There is a lot of worry about how quantum computing will impact encryption. Quantum computing’s power and speed would make brute-forcing and cracking encryption algorithms easy. This is a concern, considering then any message could be decrypted without keys, and with ease. However, quantum computing is not widely available right now and is still being experimented on. Plus, there are thoughts about how encryption may be positively influenced by quantum computing. There is a lot of nuance, and I am not an expert in this field. Refer to other sources on this discussion, and make your own informed opinions. 
