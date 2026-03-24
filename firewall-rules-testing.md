# Firewall Rules Testing

El objetivo de estas pruebas es verificar el correcto funcionamiento de las reglas definidas en el firewall y como se muestran en el dashboard de Wazuh.

---
## Reglas de la interfaz WAN

#### WAN -> DMZ TCP 3000 = PASS: Tracking ID 1769487539 

Desde el navegador se accede a la URL de el servidor web en el puerto 3000.

<img  alt="image" src="images/test-id-1769487539.png" /> 

Se evidencia que el firewall registró la acción.

<img  alt="image" src="images/log-id-1769487539.png" /> 

#### BLOCK Todo desde WAN:  Tracking ID 1769488056

Desde un navegador fuera de la red de Virtualbox intento acceder a la IP de el firewall usando el puerto 443.

<img width="729" height="485" alt="image" src="/images/test-id-1769488056.png" /> 

Se evidencia que el firewall bloqueo el trafico desde WAN al puerto 80.

<img  alt="image" src="images/log-id-1769488056.png" /> 

---

## Reglas de la interfaz DMZ

#### DMZ -> LAN = BLOCK: Tracking ID 1769407069

Hago ping desde el server en DMZ al cliente en LAN

<img  alt="image" src="images/test-id-1769407069.png" /> 

Se refleja el log del paquete de ICMP en Wazuh

<img  alt="image" src="images/log-id-1769407069.png" /> 

#### DMZ -> WAN = PASS: Tracking ID 1769487015

Hago ping desde DMZ a google.com

<img  alt="image" src="images/test-id-1769487015.png" /> 

En Wazuh se refleja el log al DNS de Google

<img  alt="image" src="images/log-id-1769487015.png" /> 

---

## Reglas de la interfaz LAN

#### Debian Admin -> Wazuh Dashboard: Tracking ID 1771559538

Accedo al dashboard de Wazuh desde el debian en LAN

<img  alt="image" src="images/test-id-1771559538.png" /> 

Log en el dashboard de Wazuh

<img  alt="image" src="images/log-id-1771559538.png" /> 

#### 172.16.0.10 -> 10.0.0.50 TCP 22 = PASS: Tracking ID 1769488682

Accedo por SSH al server desde el debian cliente en LAN

<img  alt="image" src="images/test-id-1769499682.png" /> 

Log en el dashboard de Wazuh

<img  alt="image" src="images/log-id-1769499682.png" /> 

#### LAN -> DMZ = BLOCK: Tracking ID  1769488878

Intento acceder a la aplicación web en DMZ

<img  alt="image" src="images/test-id-1769488878.png" />

Log en el dashboard de Wazuh

<img  alt="image" src="images/log-id-1769488878.png" />

---

## Conclusión

Las reglas evaluadas cumplen su función y ademas se están logeando exitosamente en Wazuh, lo cual permite hacer seguimiento de el trafico que es filtrado por el firewall.