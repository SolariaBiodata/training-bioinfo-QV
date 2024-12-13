# **Configuración Inicial de Acceso a Servidores en la Nube**

El acceso inicial a servidores en la nube es un paso fundamental para aprovechar los servicios de infraestructura ofrecidos por proveedores como AWS, Azure, Google Cloud o DigitalOcean. Una configuración adecuada asegura tanto la operatividad del servidor como su seguridad. Este proceso involucra desde la elección del proveedor hasta las configuraciones de red y la generación de claves de acceso.

## **Creación de una cuenta en proveedores de nube**
El primer paso para configurar un servidor en la nube es seleccionar un proveedor adecuado según las necesidades del proyecto. Algunos factores a considerar son el costo, la facilidad de uso, las regiones disponibles y los servicios adicionales ofrecidos. Una vez seleccionado el proveedor, se debe:
- Crear una cuenta en la plataforma elegida.
- Completar el proceso de registro, que generalmente incluye la verificación de identidad mediante correo electrónico, número de teléfono y una tarjeta de crédito válida.
- Familiarizarse con el panel de control, que será la interfaz principal para administrar servidores y recursos.

## **Elección de máquina virtual y especificaciones**
Una vez creada la cuenta, es necesario seleccionar la máquina virtual que alojará el servidor:
- **Tipos de instancias**: Se pueden elegir instancias estándar para usos generales, optimizadas para cómputo intensivo, memoria o almacenamiento, dependiendo de las necesidades del proyecto.
- **Especificaciones básicas**: Definir cuántos CPUs virtuales, memoria RAM y almacenamiento serán necesarios. Es importante prever las necesidades futuras para evitar sobrecostos.
- **Sistema operativo**: Seleccionar una imagen base, como Ubuntu, CentOS o Windows Server, según las aplicaciones que se planean ejecutar en el servidor.

Además, se recomienda elegir una región cercana a los usuarios finales para optimizar el rendimiento.

## **Generación de claves SSH para acceso seguro**
El protocolo SSH es el estándar para acceder a servidores de manera remota y segura. Configurar claves SSH implica:
1. **Generar las claves**: 
   - En sistemas Linux/MacOS: 
     ```bash
     ssh-keygen -t rsa -b 4096 -C "tu_correo@example.com"
     ```
   - En sistemas Windows: Usar herramientas como PuTTYgen o el cliente SSH integrado.
2. **Guardar la clave privada**: Esta clave debe mantenerse segura en el equipo local y nunca compartirse.
3. **Subir la clave pública al servidor**: Durante la configuración del servidor, el proveedor de nube pedirá esta clave para autorizar accesos futuros.

## **Configuración inicial de red y seguridad**
Proteger el servidor desde el inicio es crucial para evitar accesos no autorizados. Los pasos incluyen:
- **Reglas de firewall**: Configurar el acceso solo a los puertos necesarios. Por ejemplo:
  - Puerto 22 para conexiones SSH.
  - Puerto 3389 si se usará Remote Desktop Protocol (RDP).
- **Restricción de acceso por IP**: Especificar una lista blanca de direcciones IP permitidas.
- **Asignación de IP**: Decidir si el servidor tendrá una dirección IP pública dinámica o estática.



## **Verificación del acceso inicial**
Una vez configurado el servidor y sus reglas de red, se debe probar la conectividad. Los pasos son:
1. Utilizar un cliente SSH desde el equipo local:
   ```bash
   ssh -i "ruta_a_la_clave_privada" usuario@direccion_ip
   ```
2. Verificar que se pueda acceder al servidor sin problemas.
3. Comprobar que el firewall esté bloqueando accesos no autorizados.

Configurar un servidor en la nube es un proceso esencial que requiere atención a los detalles de seguridad y funcionalidad. Una correcta generación de claves SSH, combinada con reglas de red adecuadas, garantiza que el servidor esté operativo y protegido desde el inicio. Este proceso establece una base sólida para implementar aplicaciones y servicios en un entorno confiable.

#### [Menú Principal](../../index.md)
#### [Índice](./index.md)
#### [Siguiente](./04_Protocolosdeconexion.md)