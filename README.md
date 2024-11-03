
# Taller de Infraestructura CITC 2024

En este taller trabajaremos con la infraestructura representada en los siguientes diagramas:

1. **Diagrama de Desarrollo**: Utilizaremos una configuración de dos servidores, como se muestra a continuación:
   ![Diagrama de dos servidores](./assets/img/infra-2-servers.png)

2. **Diagrama de Flujo Completo**: Este diagrama describe el flujo completo, desde la carga del codigo al repositorio hasta el despliegue en el servidor. Dependiendo de si el código se sube al branch `develop` o `main`, se implementará en el servidor de desarrollo o producción, respectivamente:
   ![Diagrama de flujo completo](./assets/img/all-flow.png)

## Requisitos de Configuración

### Instalación de Docker
Ejecute los siguientes comandos para instalar y habilitar Docker en su sistema:

```bash
curl -fsSL https://get.docker.com -o install-docker.sh
sudo sh install-docker.sh

sudo systemctl enable docker.service
sudo systemctl enable containerd.service
```

### Creación y Configuración del Usuario `deploy`
1. **Crear un usuario llamado `deploy`**:
   ```bash
   sudo adduser deploy
   sudo usermod -aG docker deploy
   sudo su - deploy
   ```

2. **Configurar una red de Docker para Traefik**:
   ```bash
   docker network create traefik-net
   ```

3. **Generar una clave SSH**:
   ```bash
   ssh-keygen -t ed25519 -C "TU_CORREO@ejemplo.com"
   ```

4. **Copiar la clave SSH pública**:
   Ejecute el siguiente comando para visualizar y copiar el contenido de la clave SSH pública generada. Esto será útil para integraciones posteriores:
   ```bash
   cat ~/.ssh/id_ed25519.pub
   ```

### Configuración de Acceso SSH en GitHub
Para permitir la autenticación mediante SSH en GitHub:

1. Visite [este enlace para crear un nuevo token de acceso en GitHub](https://github.com/settings/tokens/new).
2. Configure un token con los permisos necesarios para despliegues, como se muestra en la siguiente imagen:

   ![Token de despliegue](./assets/img/deploy-packages-token.png)