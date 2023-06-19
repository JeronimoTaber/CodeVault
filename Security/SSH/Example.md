# ENGLISH
Example 1: Connecting to a remote server via SSH

```bash
ssh username@hostname
```

Replace `username` with your actual username and `hostname` with the remote server's IP address or domain name.

Example 2: Executing a command on a remote server via SSH

```bash
ssh username@hostname command
```

Replace `username` with your username, `hostname` with the remote server's IP address or domain name, and `command` with the desired command to execute on the remote server.

Example 3: Copying files from a local machine to a remote server via SSH using the SCP command or Secure copy protocol

```bash
scp local_file_path username@hostname:remote_directory
```

Replace `local_file_path` with the path to the local file you want to copy, `username` with your username, `hostname` with the remote server's IP address or domain name, and `remote_directory` with the destination directory on the remote server.

Example 4: Copying files from a remote server to a local machine via SSH

```bash
scp username@hostname:remote_file_path local_directory
```

Replace `username` with your username, `hostname` with the remote server's IP address or domain name, `remote_file_path` with the path to the remote file you want to copy, and `local_directory` with the destination directory on your local machine.

These examples demonstrate the usage of SSH commands in a Linux environment to establish a connection, execute commands remotely, and transfer files securely.

# SPANISH

Ejemplo 1: Conectarse a un servidor remoto a través de SSH

```bash
ssh usuario@nombre_de_host
```

Reemplaza `usuario` con tu nombre de usuario real y `nombre_de_host` con la dirección IP o el nombre de dominio del servidor remoto.

Ejemplo 2: Ejecutar un comando en un servidor remoto a través de SSH

```bash
ssh usuario@nombre_de_host comando
```

Reemplaza `usuario` con tu nombre de usuario, `nombre_de_host` con la dirección IP o el nombre de dominio del servidor remoto y `comando` con el comando que deseas ejecutar en el servidor remoto.

Ejemplo 3: Copiar archivos desde una máquina local a un servidor remoto a través de SSH usando el comando SCP o Secure copy protocol

```bash
scp ruta_del_archivo_local usuario@nombre_de_host:directorio_remoto
```

Reemplaza `ruta_del_archivo_local` con la ruta al archivo local que deseas copiar, `usuario` con tu nombre de usuario, `nombre_de_host` con la dirección IP o el nombre de dominio del servidor remoto y `directorio_remoto` con el directorio de destino en el servidor remoto.

Ejemplo 4: Copiar archivos desde un servidor remoto a una máquina local a través de SSH

```bash
scp usuario@nombre_de_host:ruta_del_archivo_remoto directorio_local
```

Reemplaza `usuario` con tu nombre de usuario, `nombre_de_host` con la dirección IP o el nombre de dominio del servidor remoto, `ruta_del_archivo_remoto` con la ruta al archivo remoto que deseas copiar y `directorio_local` con el directorio de destino en tu máquina local.

Estos ejemplos demuestran el uso de comandos SSH en un entorno Linux para establecer una conexión, ejecutar comandos de forma remota y transferir archivos de manera segura.