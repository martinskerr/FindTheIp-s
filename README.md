# FindTheIp-s
Python Script that found all the ip in your network red

Este código utiliza la librería Scapy para enviar un paquete ARP (Address Resolution Protocol) a todos los dispositivos conectados en 
una red específica. ARP es un protocolo de red que permite a los dispositivos en una red local determinar la dirección MAC (Media Access Control) 
de otro dispositivo conociendo su dirección IP.
La línea "net_addr = "192.168.0.2/24"" define la dirección de red y la máscara de red que se va a escanear.
La línea "arp = ARP(pdst=net_addr)" crea un paquete ARP con la dirección de destino especificada en "net_addr".
La línea "ether = Ether(dst="ff:ff:ff:ff:ff:ff")" crea un paquete Ethernet con una dirección de destino especial "ff:ff:ff:ff:ff:ff" 
que se utiliza para enviar un mensaje a todos los dispositivos en la red.
La línea "packet = ether/arp" combina ambos paquetes Ethernet y ARP en un solo paquete.
La línea "result = srp(packet, timeout=3, verbose=0)[0]" envía el paquete creado anteriormente a
todos los dispositivos de la red y recolecta las respuestas en la variable "result".
El ciclo "for sent, received in result:" recorre las respuestas recibidas y utiliza la función "socket.gethostbyaddr()" 
para obtener el nombre del host a partir de la dirección IP recibida. Si no se puede obtener el nombre del host, 
se imprime "Unknown". Finalmente se imprime la dirección IP, el nombre del host y la dirección MAC de cada dispositivo conectado.
