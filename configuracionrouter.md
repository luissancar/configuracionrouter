# Configuración router Cisco 1841
- Añadir los módulos HWIC-4ESW y WIC-2T.
- Los routers se conectarán desde el puerto serial con el cable serial DCE.
![Con titulo](http://www.cisco.com/c/dam/en/us/support/docs/wan/x25-protocols/7921-x25-back1.gif "titulo")  

Los DCE y DTE se utilizan en conexiones WAN. La comunicación mediante una conexión WAN se mantiene al proporcionar una frecuencia de reloj aceptable tanto para el dispositivo receptor como el emisor. En la mayoría de los casos, la compañía telefónica o ISP proporciona el servicio de temporización que sincroniza la señal transmitida.
Por defecto, los Routers son dispositivos DTE, pero se los puede configurar de manera tal que actúen como dispositivos DCE.
- Configurar las ips de los puertos ethernet y serie). Entramos en el terminal del router:
  - enable -> entra en modo privilegiado.
  - configure terminal
  - hostname nombrerouter
  - interface fa0/0
  - ip address 192.168.1.1 255.255.255.0
  - no shutdown ->  "guarda" los cambios
  - exit -> sale configuración fa0/0
  - interface se0/0/0
  - ip address 10.0.1.1 255.255.255.0
  - clock rate 64000 -> sincroniza reloj
  - no shutdown
  - end
  - copy running-config startup-config  -> guarda definitivamente.     
- Configuración enrutamiento dinámico. Entramos en el terminal del router:
    - enable -> entra en modo privilegiado.
    - show ip route -> ver conexiones
    - configure terminal
    - router rip
    - version 2
    - network 192.168.1.0
    - network 10.0.1.0
    - do write
    - exit
    - exit
    - show ip protocols
