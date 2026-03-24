# SOC Practices — Homelab

Repositorio de documentación técnica correspondiente a practicas realizadas en un entorno de laboratorio que simula la infraestructura y operaciones de un Centro de Operaciones de Seguridad (SOC).

---
## Practicas documentadas

### Pruebas de reglas de firewall

Se validaron reglas sobre las tres interfaces del firewall (WAN, DMZ y LAN), verificando tanto el comportamiento esperado del trafico como el correcto registro de eventos en el dashboard de Wazuh.

Las pruebas cubren los siguientes escenarios:

**Interfaz WAN**
- Permiso de trafico entrante desde WAN hacia DMZ por TCP/3000 (acceso al servidor web).
- Bloqueo de todo trafico entrante desde WAN no autorizado.

**Interfaz DMZ**
- Bloqueo de trafico desde DMZ hacia la red LAN (aislamiento de la zona expuesta).
- Permiso de trafico saliente desde DMZ hacia WAN (resolución DNS y conectividad a Internet).

**Interfaz LAN**
- Acceso desde el administrador Debian al dashboard de Wazuh.
- Acceso SSH desde LAN al servidor en DMZ por TCP/22.
- Bloqueo de acceso directo desde LAN hacia la aplicación web en DMZ.

Cada caso incluye evidencia del intento de conexión y del log correspondiente registrado en Wazuh.