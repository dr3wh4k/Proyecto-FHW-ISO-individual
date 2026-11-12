# 04 — Diseño de servicios de directorio

## 1. Objetivo

Analizar los servicios de directorio que pueden implantarse en la infraestructura para centralizar la administración de usuarios, equipos y recursos.

## 2. Necesidades

Un servicio de directorio permite:

- Gestionar usuarios y grupos.
- Centralizar la autenticación.
- Administrar equipos del dominio.
- Aplicar políticas de seguridad.
- Controlar el acceso a recursos compartidos.
- Simplificar la administración de la infraestructura.

## 3. Alternativas

### Active Directory Domain Services

Servicio de directorio de Microsoft integrado en Windows Server.

Características:

- Administración centralizada de usuarios y equipos.
- Integración con clientes Windows.
- Uso de dominios.
- Gestión de políticas mediante GPO.
- Integración con DNS.

### Samba 4 Active Directory Domain Controller

Implementación de servicios compatibles con Active Directory mediante Samba.

Características:

- Administración de dominios.
- Autenticación centralizada.
- Compatibilidad con clientes Windows.
- Integración con servicios Linux.

### FreeIPA

Solución de gestión de identidades orientada principalmente a entornos Linux.

Características:

- Gestión centralizada de usuarios.
- Autenticación mediante Kerberos.
- Integración con LDAP.
- Gestión de políticas y certificados.

## 4. Comparativa

| Característica | Active Directory | Samba 4 | FreeIPA |
|---|---|---|---|
| Usuarios y grupos | Sí | Sí | Sí |
| Integración Windows | Nativa | Compatible | Requiere configuración |
| Integración Linux | Sí | Sí | Nativa |
| GPO | Sí | Compatibilidad | No equivalente a GPO |
| Administración de dominio | Sí | Sí | Sí |

## 5. Decisión de implementación

La solución definitiva se determinará durante la configuración de Windows Server y los servicios de directorio.

La elección deberá tener en cuenta:

- Los requisitos del proyecto.
- La compatibilidad con Windows.
- La integración con Debian.
- Los recursos disponibles.
- La facilidad de administración.

## 6. Datos pendientes

- Nombre del dominio.
- Nombre del servidor.
- Dirección IP definitiva de Windows Server.
- Configuración DNS.
- Usuarios y grupos.
- Unidades organizativas.
- Políticas de grupo.
- Integración del cliente Windows.

## 7. Pruebas previstas

- Comprobar la resolución DNS del dominio.
- Comprobar la unión del cliente Windows al dominio.
- Iniciar sesión con un usuario del dominio.
- Comprobar las políticas aplicadas.
- Verificar los permisos de acceso a los recursos.
