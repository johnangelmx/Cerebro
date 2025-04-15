```bash
aws ec2 create-key-pair --key-name MicroserviceChat --query 'KeyMaterial' --output text > MicroserviceChat.pem
```

```bash
# Descargar el binario de GitLab Runner para tu sistema
sudo curl -L --output /usr/local/bin/gitlab-runner https://gitlab-runner-downloads.s3.amazonaws.com/latest/binaries/gitlab-runner-linux-amd64

# Darle permisos de ejecución al binario
sudo chmod +x /usr/local/bin/gitlab-runner

# No creamos un nuevo usuario, utilizamos el usuario 'ubuntu'
# Asegúrate de que el directorio home de 'ubuntu' exista, en general debería ser /home/ubuntu
# Si no está creado por alguna razón, puedes crearlo manualmente, pero lo normal es que ya exista

# Instalar y ejecutar GitLab Runner como el usuario 'ubuntu'
sudo gitlab-runner install --user=ubuntu --working-directory=/home/ubuntu
sudo gitlab-runner start

```