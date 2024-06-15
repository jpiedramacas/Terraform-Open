# Terraform README

## Introducción

Terraform es una herramienta de infraestructura como código (IaC) que permite definir y aprovisionar una infraestructura de manera declarativa y eficiente. Este README te guiará a través del proceso de instalación de Terraform y te introducirá a algunos de los comandos fundamentales.

## Instalación de Terraform

### Opción 1: Descarga desde la página oficial

1. **Accede a la página oficial de Terraform:**
   - [Página de descargas de Terraform](https://www.terraform.io/downloads)

2. **Selecciona la versión adecuada para tu sistema operativo:**
   - Descarga el archivo comprimido correspondiente (zip, tar.gz, etc.).

3. **Descomprime el archivo descargado:**
   - En Windows, puedes usar herramientas como WinRAR o 7-Zip.
   - En macOS y Linux, puedes usar el comando `tar`:
     ```sh
     tar -xzf terraform_VERSION_OS_ARCH.zip
     ```

4. **Mueve el binario de Terraform a una ubicación incluida en tu PATH:**
   - En Windows:
     ```sh
     move terraform.exe C:\Windows\System32\
     ```
   - En macOS y Linux:
     ```sh
     sudo mv terraform /usr/local/bin/
     ```

5. **Verifica la instalación:**
   ```sh
   terraform -v
   ```

### Opción 2: Instalación usando Chocolatey (Windows)

1. **Instala Chocolatey:**
   - Abre una ventana de PowerShell con privilegios de administrador y ejecuta:
     ```sh
     Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))
     ```

2. **Instala Terraform usando Chocolatey:**
   - Ejecuta el siguiente comando en PowerShell con privilegios de administrador:
     ```sh
     choco install terraform
     ```

3. **Verifica la instalación:**
   ```sh
   terraform -v
   ```

## Comandos Fundamentales en Terraform

### 1. Inicialización del Proyecto

Antes de usar Terraform, debes inicializar tu proyecto. Esto descarga los proveedores necesarios y configura el entorno de trabajo.

```sh
terraform init
```

### 2. Planificación de Cambios

Este comando genera y muestra un plan de ejecución, que describe los cambios que Terraform hará en la infraestructura.

```sh
terraform plan
```

### 3. Aplicación de Cambios

Aplica los cambios necesarios para alcanzar el estado deseado de la configuración definida en los archivos de Terraform.

```sh
terraform apply
```
- Para aplicar automáticamente los cambios sin solicitar confirmación, usa la opción `-auto-approve`:
  ```sh
  terraform apply -auto-approve
  ```

### 4. Destrucción de la Infraestructura

Destruye toda la infraestructura administrada por Terraform.

```sh
terraform destroy
```
- Para destruir automáticamente sin solicitar confirmación, usa la opción `-auto-approve`:
  ```sh
  terraform destroy -auto-approve
  ```

### 5. Visualización del Estado

Muestra el estado actual de la infraestructura administrada por Terraform.

```sh
terraform show
```

### 6. Inspección del Estado

Muestra una lista más detallada de todos los recursos administrados por Terraform.

```sh
terraform state list
```

### 7. Extracción de Información de un Recurso Específico

Muestra información detallada sobre un recurso específico administrado por Terraform.

```sh
terraform state show <RESOURCE_NAME>
```

### 8. Validación de Configuración

Valida la sintaxis y la estructura de los archivos de configuración de Terraform sin aplicar cambios.

```sh
terraform validate
```

### 9. Formateo de Archivos de Configuración

Formatea todos los archivos de configuración de Terraform en el directorio actual para que sigan un estilo de código coherente.

```sh
terraform fmt
```

## Conclusión

Este README te ha proporcionado una guía detallada sobre cómo instalar Terraform y te ha introducido a algunos de los comandos más importantes. Para más información, puedes consultar la [documentación oficial de Terraform](https://www.terraform.io/docs). ¡Feliz aprovisionamiento de infraestructura!
