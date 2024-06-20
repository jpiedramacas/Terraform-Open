# Terraform.tf

## Introducción

Terraform es una herramienta de infraestructura como código (IaC) que permite definir y aprovisionar una infraestructura de manera declarativa y eficiente. Este README te guiará a través del proceso de instalación de Terraform y te introducirá a algunos de los comandos fundamentales.

## Instalación de Terraform

### Opción 1: Descarga desde la página oficial

1. **Accede a la página oficial de Terraform:**
   - [Terraform](https://www.terraform.io/downloads)

### Opción 2: Instalación usando Chocolatey (Windows)

1. **Instala Chocolatey:**
   - Abre una ventana de PowerShell con privilegios de administrador y ejecuta:
     ```sh
     Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))
     ```
   - Desde la página oficial [Chocolatey](https://chocolatey.org/install)
     
2. **Instala Terraform usando Chocolatey:**
   - Ejecuta el siguiente comando en PowerShell con privilegios de administrador:
     ```sh
     choco install terraform -y
     ```

3. **Verifica la instalación:**
   ```sh
   terraform -v
   ```
### Opción 3: Amazon Linux

1. **Actualiza el sistema operativo:**
   Este comando asegurará que todos los paquetes instalados estén actualizados.

   ```bash
   sudo yum update -y
   ```

2. **Instala `yum-config-manager`:**
   Esto es necesario para agregar y administrar nuevos repositorios.

   ```bash
   sudo yum install -y yum-utils
   ```

3. **Agrega el repositorio de HashiCorp:**
   HashiCorp proporciona un repositorio oficial para Amazon Linux, que facilita la instalación y actualización de Terraform.

   ```bash
   sudo yum-config-manager --add-repo https://rpm.releases.hashicorp.com/AmazonLinux/hashicorp.repo
   ```

4. **Instala Terraform:**
   Este comando instalará Terraform desde el repositorio que acabas de agregar.

   ```bash
   sudo yum install -y terraform
   ```

5. **Verifica la instalación:**
   Asegúrate de que Terraform se haya instalado correctamente y verifica la versión instalada.

   ```bash
   terraform -version
   ```

## Comandos Fundamentales en Terraform

Para ver todos los comandos de Terraform

```sh
terraform 
```

Podemos observar los comandos y una pequeña explicaciñon de ellos, tiene que aparecerte algo asi: 
```sh
$ terraform
Usage: terraform [global options] <subcommand> [args]

The available commands for execution are listed below.
The primary workflow commands are given first, followed by
less common or more advanced commands.

Main commands:
  init          Prepare your working directory for other commands
  validate      Check whether the configuration is valid
  plan          Show changes required by the current configuration
  apply         Create or update infrastructure
  destroy       Destroy previously-created infrastructure

```

### 1. Inicialización del Proyecto

Antes de usar Terraform, debes inicializar tu proyecto. Este comando descarga los proveedores necesarios y configura el entorno de trabajo para Terraform.

```sh
terraform init
```

#### Explicación del Comando

- `terraform init` configura tu directorio de trabajo como un directorio de proyecto de Terraform.
- Descarga los plugins del proveedor especificados en tus archivos de configuración.
- Configura el backend donde se almacenará el estado de tu infraestructura.

### 2. Planificación de Cambios

Este comando genera y muestra un plan de ejecución, que describe los cambios que Terraform hará en la infraestructura basándose en tu configuración actual.

```sh
terraform plan
```

#### Explicación del Comando

- `terraform plan` examina tus archivos de configuración y el estado actual de la infraestructura.
- Muestra un plan detallado de las acciones que Terraform tomará para hacer coincidir la infraestructura con la configuración.
- No realiza ningún cambio en la infraestructura, solo muestra el plan.

### 3. Aplicación de Cambios

Aplica los cambios necesarios para alcanzar el estado deseado de la configuración definida en los archivos de Terraform.

```sh
terraform apply
```

#### Explicación del Comando

- `terraform apply` ejecuta el plan generado por `terraform plan`.
- Aplica los cambios necesarios para crear, actualizar o eliminar recursos según sea necesario.
- Solicita confirmación antes de aplicar los cambios. Para evitar la solicitud de confirmación, usa la opción `-auto-approve`:
  ```sh
  terraform apply -auto-approve
  ```

### 4. Destrucción de la Infraestructura

Destruye toda la infraestructura administrada por Terraform.

```sh
terraform destroy
```

#### Explicación del Comando

- `terraform destroy` elimina todos los recursos definidos en tus archivos de configuración.
- Solicita confirmación antes de destruir los recursos. Para evitar la solicitud de confirmación, usa la opción `-auto-approve`:
  ```sh
  terraform destroy -auto-approve
  ```

### 5. Visualización del Estado

Muestra el estado actual de la infraestructura administrada por Terraform.

```sh
terraform show
```

#### Explicación del Comando

- `terraform show` muestra detalles del estado actual almacenado de la infraestructura.
- Proporciona una visión detallada de todos los recursos y sus configuraciones actuales.

### 6. Inspección del Estado

Muestra una lista más detallada de todos los recursos administrados por Terraform.

```sh
terraform state list
```

#### Explicación del Comando

- `terraform state list` muestra una lista de todos los recursos en el estado de Terraform.
- Útil para ver rápidamente qué recursos están siendo gestionados por Terraform.

### 7. Extracción de Información de un Recurso Específico

Muestra información detallada sobre un recurso específico administrado por Terraform.

```sh
terraform state show <RESOURCE_NAME>
```

#### Explicación del Comando

- `terraform state show <RESOURCE_NAME>` proporciona detalles completos sobre un recurso específico.
- Reemplaza `<RESOURCE_NAME>` con el nombre del recurso que quieres inspeccionar.

### 8. Validación de Configuración

Valida la sintaxis y la estructura de los archivos de configuración de Terraform sin aplicar cambios.

```sh
terraform validate
```

#### Explicación del Comando

- `terraform validate` comprueba la validez de tus archivos de configuración.
- Asegura que la sintaxis es correcta y que las configuraciones son coherentes y válidas.

### 9. Formateo de Archivos de Configuración

Formatea todos los archivos de configuración de Terraform en el directorio actual para que sigan un estilo de código coherente.

```sh
terraform fmt
```

#### Explicación del Comando

- `terraform fmt` reescribe tus archivos de configuración para que sigan las convenciones de estilo estándar de Terraform.
- Mejora la legibilidad y coherencia del código.

---

Estos comandos fundamentales de Terraform te permitirán gestionar y mantener tu infraestructura de manera eficiente. Cada comando tiene su función específica y conocerlos te ayudará a aprovechar al máximo las capacidades de Terraform.
## Conclusión

Este README te ha proporcionado una guía detallada sobre cómo instalar Terraform y te ha introducido a algunos de los comandos más importantes. Para más información, puedes consultar la [documentación oficial de Terraform](https://www.terraform.io/docs). ¡Feliz aprovisionamiento de infraestructura!
