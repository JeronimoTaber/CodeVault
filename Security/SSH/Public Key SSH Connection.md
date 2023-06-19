# ENGLISH

Below is an illustrative guide on implementing public key authentication for secure SSH connectivity to a server, eliminating the need for passwords.


1. Generate a new SSH key pair using the following command:
    
	```bash
ssh-keygen -t rsa
	```

    This will generate a new RSA key pair with the default settings.

2. You will be prompted to provide a file name for saving the key. Press Enter to accept the default location (`~/.ssh/id_rsa`), or provide a custom file name if desired.
    
3. Next, you will be prompted to enter a passphrase. You can either enter a passphrase for added security or leave it blank for no passphrase. Press Enter after making your choice.
    
4. The key pair will be generated. Two files will be created: `id_rsa` (private key) and `id_rsa.pub` (public key).
    
5. Now, copy the public key (`id_rsa.pub`) to the remote server where you want to log in using SSH. You can do this by running the following command:
    
	```bash
	ssh-copy-id username@server_ip
	``` 
    Replace `username` with your username on the remote server and `server_ip` with the IP address or hostname of the remote server. You will be prompted to enter your password for authentication.
	
    This command will copy the public key to the remote server and automatically add it to the `authorized_keys` file in the remote server's `~/.ssh` directory.
	
    Note: If the `ssh-copy-id` command is not available on your system, you can manually copy the contents of the `id_rsa.pub` file and append them to the `~/.ssh/authorized_keys` file on the remote server.

6. Once the public key is added to the `authorized_keys` file on the remote server, you can now log in to the server using SSH without entering a password. Run the following command:
    
	```bash
	ssh username@server_ip
	``` 
    Replace `username` with your username on the remote server and `server_ip` with the IP address or hostname of the remote server.
	  
    If you set a passphrase for your private key, you will be prompted to enter it.

7. To avoid entering the passphrase every time you use SSH, you can add the private key to the SSH agent by running the following command:
    
	```bash
	ssh-add ~/.ssh/id_rsa
	``` 
    This will add the private key to the SSH agent, and you won't be prompted for the passphrase again until you restart your system or remove the key from the agent.
    

That's it! You have now generated a public key in Linux, added it to the remote server's `authorized_keys` file, and successfully logged in to the server using SSH without entering a password.

# SPANISH
A continuación se muestra una guía ilustrativa sobre cómo implementar la autenticación de clave pública para lograr una conexión SSH segura a un servidor, eliminando la necesidad de contraseñas.

1. Genera un nuevo par de claves SSH con el siguiente comando:
    
    ```bash
    ssh-keygen -t rsa
    ```
    
    Esto generará un nuevo par de claves RSA con la configuración predeterminada.
    
2. Se te pedirá que indiques un nombre de archivo para guardar la clave. Presiona Enter para aceptar la ubicación y nombre de archivo predeterminados (`~/.ssh/id_rsa`), o proporciona un nombre de archivo personalizado si lo deseas.
    
3. A continuación, se te pedirá que ingreses una frase de contraseña. Puedes ingresar una frase de contraseña para agregar seguridad adicional o dejarla en blanco para no usar una contraseña. Presiona Enter después de tomar tu decisión.
    
4. Se generará el par de claves y se guardarán dos archivos: `id_rsa` (clave privada) y `id_rsa.pub` (clave pública).
    
5. Ahora, copia la clave pública (`id_rsa.pub`) al servidor remoto donde deseas iniciar sesión mediante SSH. Puedes hacer esto ejecutando el siguiente comando:
    
    ```bash
    ssh-copy-id usuario@ip_del_servidor
    ```
    Reemplaza `usuario` con tu nombre de usuario en el servidor remoto y `ip_del_servidor` con la dirección IP o el nombre de host del servidor remoto. Se te pedirá que ingreses tu contraseña para autenticarte.
    
    Este comando copiará la clave pública al servidor remoto y la agregará automáticamente al archivo `authorized_keys` en el directorio `~/.ssh` del servidor remoto.
    
    Nota: Si el comando `ssh-copy-id` no está disponible en tu sistema, puedes copiar manualmente el contenido del archivo `id_rsa.pub` y agregarlo al final del archivo `authorized_keys` en el servidor remoto.
    
6. Una vez que se haya agregado la clave pública al archivo `authorized_keys` en el servidor remoto, ahora puedes iniciar sesión en el servidor sin ingresar una contraseña. Ejecuta el siguiente comando:
    
	```bash
    ssh usuario@ip_del_servidor
    ```
    Reemplaza `usuario` con tu nombre de usuario en el servidor remoto y `ip_del_servidor` con la dirección IP o el nombre de host del servidor remoto.
    
    Si configuraste una frase de contraseña para tu clave privada, se te solicitará que la ingreses.
    
7. Para evitar tener que ingresar la frase de contraseña cada vez que uses SSH, puedes agregar la clave privada al agente SSH.
    
    Ejecuta el siguiente comando para agregar la clave privada al agente SSH:
    
    ```bash
    ssh-add ~/.ssh/id_rsa
    ```
    
    Esto agregará la clave privada al agente SSH, y no se te solicitará la frase de contraseña nuevamente hasta que reinicies el sistema o elimines la clave del agente.
    

¡Eso es todo! Ahora has generado una clave pública en Linux, la has agregado al archivo `authorized_keys` del servidor remoto e iniciado sesión con éxito en el servidor usando SSH sin ingresar una contraseña.