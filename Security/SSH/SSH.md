# ENGLISH
## SSH (Secure Shell) 

### Description 

SSH (Secure Shell) is a secure network protocol used to establish encrypted and secure connections over an insecure network. It provides a mechanism for securely accessing and remotely controlling systems and servers, thereby avoiding the exposure of confidential information and ensuring the integrity of transmitted data.

The SSH protocol utilizes asymmetric cryptography techniques to authenticate and encrypt communication between the client and the server. This means that both the client and the server have a public key and a private key. The public key is shared with the remote server, while the private key is kept secret on the client. During the authentication process, the server verifies the client's identity using the corresponding public key. Once the connection is established, symmetric encryption is used to protect the confidentiality of the transmitted data.

### Advantages of SSH 

- **Security:** SSH employs robust encryption techniques to protect communication against eavesdropping and data manipulation attacks. This ensures that transmitted information, such as passwords and sensitive data, is safeguarded against unauthorized access.

- **Authentication:** SSH uses public-key and private-key pairs for authentication, providing an additional level of security compared to password-based authentication methods. This makes it more difficult for attackers to compromise authentication credentials.

- **Secure Remote Access:** SSH allows remote access and control of systems and servers, which is particularly useful in environments where systems are located in different geographical locations. By establishing an SSH connection, users can interact with remote systems as if they were physically in front of them.

- **Secure File Transfer:** In addition to remote access, SSH also provides secure file transfer capabilities through the use of programs like SCP (Secure Copy) or SFTP (Secure File Transfer Protocol). This enables users to transfer files between systems securely and encrypted.


### How the encryption works in SSH:

**1. Key Exchange:** During the initial connection, SSH performs a key exchange protocol to establish a secure channel. This involves negotiating encryption algorithms, exchanging cryptographic keys, and generating a shared secret key for further communication.
    
**2. Asymmetric Encryption:** SSH uses asymmetric cryptography, typically based on the RSA or DSA algorithms, to authenticate the server and optionally the client. The server has a private key that is kept securely, and the corresponding public key is distributed and trusted by clients. When a client connects to a server, the server presents its public key for authentication. The client verifies the authenticity of the server by checking its digital signature using the trusted public key.
    
**3. Symmetric Encryption:** After the key exchange and authentication, SSH switches to symmetric encryption for data transmission. A symmetric encryption algorithm like AES (Advanced Encryption Standard) is used to encrypt the actual data. The symmetric key, which is derived from the shared secret key established during the key exchange, is used for encryption and decryption at both ends.
    
**4. Message Integrity:** To ensure the integrity of the data, SSH employs cryptographic hash functions like SHA-1 or SHA-256. Each packet sent over the encrypted channel includes a MAC (Message Authentication Code), which is calculated based on the packet's contents and a secret key. The recipient can verify the integrity of the received packets by recalculating the MAC and comparing it with the received MAC.
    
**5. Diffie-Hellman Key Exchange:** SSH also supports Diffie-Hellman key exchange, which allows the client and server to independently generate a shared secret key over an insecure channel without exchanging the key directly. This ensures that even if an attacker intercepts the communication, they cannot deduce the shared secret key.
    

By combining asymmetric encryption for authentication and symmetric encryption for data transmission, SSH provides secure and encrypted communication between the client and the server. This prevents eavesdropping, data tampering, and unauthorized access to sensitive information during SSH sessions.

# SPANISH
## SSH (Secure Shell)

### Descripción

SSH (Secure Shell) es un protocolo de red seguro utilizado para establecer conexiones seguras y cifradas a través de una red no segura. Proporciona un mecanismo para acceder y controlar de forma remota sistemas y servidores de manera segura, evitando así la exposición de información confidencial y garantizando la integridad de los datos transmitidos.

El protocolo SSH utiliza técnicas de criptografía asimétrica para autenticar y cifrar la comunicación entre el cliente y el servidor. Esto significa que tanto el cliente como el servidor tienen una clave pública y una clave privada. La clave pública se comparte con el servidor remoto, mientras que la clave privada se mantiene en secreto en el cliente. Durante el proceso de autenticación, el servidor verifica la identidad del cliente utilizando la clave pública correspondiente. Una vez que se establece la conexión, se utiliza cifrado simétrico para proteger la confidencialidad de los datos transmitidos.

### Ventajas de SSH

- **Seguridad:** SSH utiliza técnicas de cifrado robustas para proteger la comunicación contra ataques de escucha y manipulación de datos. Esto asegura que la información transmitida, como contraseñas y datos confidenciales, esté protegida contra accesos no autorizados.
    
- **Autenticación:** SSH utiliza claves públicas y privadas para la autenticación, lo que proporciona un nivel adicional de seguridad en comparación con los métodos de autenticación basados en contraseñas. Esto hace que sea más difícil para los atacantes comprometer las credenciales de autenticación.
    
- **Acceso remoto seguro:** SSH permite acceder y controlar sistemas y servidores de forma remota, lo que es especialmente útil en entornos donde los sistemas están ubicados en diferentes ubicaciones geográficas. Al establecer una conexión SSH, los usuarios pueden interactuar con los sistemas remotos como si estuvieran frente a ellos físicamente.
    
- **Transferencia de archivos segura:** Además del acceso remoto, SSH también proporciona capacidades de transferencia de archivos segura a través del uso del programa SCP (Secure Copy) o SFTP (Secure File Transfer Protocol). Esto permite a los usuarios transferir archivos entre sistemas de forma segura y cifrada.


###   Cómo funciona el cifrado en SSH:

**1. Intercambio de claves:** Durante la conexión inicial, SSH realiza un protocolo de intercambio de claves para establecer un canal seguro. Esto implica negociar algoritmos de cifrado, intercambiar claves criptográficas y generar una clave secreta compartida para la comunicación posterior.

**2. Cifrado asimétrico:** SSH utiliza criptografía asimétrica, generalmente basada en los algoritmos RSA o DSA, para autenticar el servidor y, opcionalmente, el cliente. El servidor tiene una clave privada que se guarda de forma segura, y la clave pública correspondiente se distribuye y se confía en los clientes. Cuando un cliente se conecta a un servidor, el servidor presenta su clave pública para la autenticación. El cliente verifica la autenticidad del servidor comprobando su firma digital utilizando la clave pública confiable.

**3. Cifrado simétrico:** Después del intercambio de claves y la autenticación, SSH cambia al cifrado simétrico para la transmisión de datos. Se utiliza un algoritmo de cifrado simétrico como AES (Estándar de Cifrado Avanzado) para cifrar los datos reales. La clave simétrica, que se deriva de la clave secreta compartida establecida durante el intercambio de claves, se utiliza para el cifrado y descifrado en ambos extremos.

**4. Integridad de mensaje:** Para garantizar la integridad de los datos, SSH utiliza funciones de hash criptográfico como SHA-1 o SHA-256. Cada paquete enviado a través del canal cifrado incluye un MAC (Código de Autenticación de Mensaje), que se calcula en función del contenido del paquete y una clave secreta. El destinatario puede verificar la integridad de los paquetes recibidos al recalcular el MAC y compararlo con el MAC recibido.

**5. Intercambio de claves Diffie-Hellman:** SSH también admite el intercambio de claves de Diffie-Hellman, que permite que el cliente y el servidor generen de forma independiente una clave secreta compartida a través de un canal inseguro sin intercambiar la clave directamente. Esto asegura que incluso si un atacante intercepta la comunicación, no pueda deducir la clave secreta compartida.

Al combinar el cifrado asimétrico para la autenticación y el cifrado simétrico para la transmisión de datos, SSH proporciona una comunicación segura y cifrada entre el cliente y el servidor. Esto evita el espionaje, la manipulación de datos y el acceso no autorizado a información confidencial durante las sesiones de SSH.