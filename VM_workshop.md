
# Implementación Automatizada de Máquinas Virtuales Linux en Azure

Este proyecto facilita el despliegue automatizado de máquinas virtuales Linux en Microsoft Azure mediante Terraform. La arquitectura está dividida en módulos para facilitar el mantenimiento y promover la reutilización de código.

## Requisitos Iniciales

Para utilizar este proyecto necesitarás:
- Cuenta activa en Microsoft Azure
- Terraform instalado en tu equipo
- Credenciales de Azure configuradas correctamente

## Organización del Proyecto

### Módulo VM (modules/vm)

Este módulo especializado gestiona la configuración de la máquina virtual Linux y sus componentes de red:

- El archivo `main.tf` configura:
  - Configura la interfaz de red (`azurerm_network_interface`).
  - Crea una dirección IP pública (`azurerm_public_ip`).
  - Implementa la máquina virtual Linux (`azurerm_linux_virtual_machine`).
  - Configura las reglas de seguridad para acceso SSH y Ansible mediante un grupo de seguridad (`azurerm_network_security_group`).

- El archivo `variables.tf` define parámetros configurables como nombre, ubicación y credenciales.

- El archivo `outputs.tf` proporciona la IP pública de la VM desplegada.

### Directorio Principal

La configuración base del proyecto incluye:

- El archivo `main.tf` que:
  - Establece el proveedor Azure
  - Crea el grupo de recursos
  - Configura la red virtual y subred
  - Llama al módulo VM con los parámetros adecuados

- El archivo `variables.tf` con las variables globales del proyecto.

## Instrucciones de Uso

1. Iniciar Terraform:
   ```sh
   terraform init
   ```

2. Verificar la configuración:
   ```sh
   terraform validate
   ```

3. Implementar la infraestructura:
   ```sh
   terraform apply
   ```


![image](https://github.com/user-attachments/assets/d005bb45-d407-42bf-adab-fec0477b7d07)
![image](https://github.com/user-attachments/assets/dbd21a29-d7d1-4198-b363-d57bcabfbd60)


## Limpieza de Recursos

Para eliminar todos los recursos creados:
```sh
terraform destroy
```
