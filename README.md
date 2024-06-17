
---

# Proyecto de Terraform: Aprovisionamiento Básico de AWS EC2

Este proyecto de Terraform proporciona una guía detallada para aprovisionar una instancia de EC2 en AWS. Incluye todas las configuraciones necesarias y comandos para gestionar la infraestructura utilizando Terraform.

## Requisitos Previos

- Cuenta de AWS con credenciales configuradas en tu máquina.
- Terraform instalado en tu máquina local.

## Estructura del Proyecto

- `main.tf`: Archivo principal de configuración de Terraform.
- `variables.tf`: Definición de variables reutilizables.
- `terraform.tfvars`: Valores para las variables definidas.
- `outputs.tf`: Definición de valores de salida.

## Configuración

### Paso 1: Configurar el Proveedor de AWS

El primer paso es configurar el proveedor de AWS. Esto se realiza en el archivo `main.tf`, donde especificamos la región en la que queremos desplegar nuestros recursos.

```hcl
# main.tf

provider "aws" {
  region = var.region
}
```

### Paso 2: Definir Recursos

En el archivo `main.tf`, definimos los recursos que queremos crear. En este caso, crearemos una instancia de EC2.

```hcl
resource "aws_instance" "mi_instancia" {
  ami           = "ami-0c55b159cbfafe1f0" # ID de la imagen de Amazon Linux 2
  instance_type = "t2.micro"

  tags = {
    Name = "MiInstanciaTerraform"
  }
}
```

### Paso 3: Definir Variables

Para hacer nuestra configuración más flexible y reutilizable, utilizamos variables. Creamos un archivo `variables.tf` para definir estas variables.

```hcl
# variables.tf

variable "region" {
  description = "La región de AWS en la que se crearán los recursos."
  default     = "us-west-2"
}
```

### Paso 4: Proveer Valores a las Variables

Proveemos valores para las variables definidas en `variables.tf` utilizando el archivo `terraform.tfvars`.

```hcl
# terraform.tfvars

region = "us-west-2"
```

### Paso 5: Definir Valores de Salida

Definimos valores de salida en el archivo `outputs.tf` para obtener información sobre los recursos creados. En este caso, queremos obtener el ID de la instancia de EC2.

```hcl
# outputs.tf

output "instance_id" {
  description = "El ID de la instancia de EC2."
  value       = aws_instance.mi_instancia.id
}
```

## Gestión de la Infraestructura

### Inicializar el Proyecto

Antes de trabajar con Terraform, necesitamos inicializar el directorio de trabajo. Este paso descarga los plugins necesarios para interactuar con los proveedores de nube especificados en la configuración.

```sh
terraform init
```

### Planificar los Cambios

Generamos un plan de ejecución para prever los cambios que se harán en la infraestructura. Este comando muestra un resumen de las acciones que Terraform tomará para alcanzar el estado deseado definido en la configuración.

```sh
terraform plan
```

Revisa el plan cuidadosamente para asegurarte de que los cambios propuestos sean los esperados.

### Aplicar los Cambios

Después de revisar y confirmar el plan, aplicamos los cambios para aprovisionar los recursos.

```sh
terraform apply
```

Terraform te pedirá confirmación antes de proceder. Escribe `yes` para confirmar. Este comando comenzará a crear los recursos definidos en `main.tf`.

### Verificar el Estado

Una vez que los recursos están aprovisionados, podemos verificar el estado actual de la infraestructura utilizando el siguiente comando:

```sh
terraform show
```

Este comando muestra información detallada sobre los recursos gestionados por Terraform.

### Destruir la Infraestructura

Cuando ya no necesitemos los recursos, podemos destruirlos usando el siguiente comando:

```sh
terraform destroy
```

Terraform te pedirá confirmación antes de destruir los recursos. Escribe `yes` para confirmar. Este comando eliminará todos los recursos definidos en tu configuración.

## Resumen de Comandos

1. **Inicializar el Proyecto**: `terraform init`
2. **Planificar los Cambios**: `terraform plan`
3. **Aplicar los Cambios**: `terraform apply`
4. **Verificar el Estado**: `terraform show`
5. **Destruir la Infraestructura**: `terraform destroy`

---

