# Pasos A Seguir

La siguiente línea de código genera un par de claves de seguridad SSH usando el algoritmo Ed25519 y agrega un comentario con una dirección de correo electrónico para identificar la clave. Esta clave se puede utilizar para autenticar a un usuario al conectarse a un servidor remoto a través de SSH.

```Bash
ssh-keygen -t ed25519 -C "Your-Email"  
```

La siguiente línea de comando inicia un agente de autenticación SSH y configura las variables de entorno para que la Shell actual pueda comunicarse con él. Esto permite utilizar claves de cifrado SSH para autenticar a los usuarios cuando se conectan a servidores remotos a través de SSH.

```Shell
eval "$(ssh-agent -s)"
```

La siguiente línea de código agrega una clave SSH al agente de autenticación SSH para que se pueda utilizar para autenticar al usuario en servidores remotos a través de SSH.
```Shell
ssh-add ~/.ssh/id_ed25519  
```

La siguiente línea de código muestra las claves SSH actualmente agregadas al agente de autenticación SSH en formato SHA-256. Esto permite verificar las claves SSH disponibles para la autenticación de un usuario en servidores remotos.
```Shell
ssh-add -l -E sha256  
```

La siguiente línea de comando muestra el contenido del archivo que contiene la clave pública de autenticación SSH correspondiente a la clave privada `id_ed25519` del usuario actual. Esto es útil para copiar y pegar la clave pública en servidores remotos para habilitar la autenticación SSH basada en clave.
```Shell
cat ~/.ssh/id_ed25519.pub
```
  
## ¿Dónde Ingresar El Resultado De `cat`?
GitHub->configuraciones->SSH and GPG Keys -> New Key