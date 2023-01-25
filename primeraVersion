from scapy.all import ARP, Ether, srp
import socket

# Define la dirección de red y la máscara de red
net_addr = "192.168.0.2/24"


# Crea un paquete ARP
arp = ARP(pdst=net_addr)
ether = Ether(dst="ff:ff:ff:ff:ff:ff")
packet = ether/arp

# Envía el paquete ARP a todos los dispositivos de la red
result = srp(packet, timeout=3, verbose=0)[0]

# Imprime la dirección IP, el nombre del host y la dirección MAC de cada dispositivo conectado
print("IP\t\t\tHostname\t\tMAC")
for sent, received in result:
    try:
        hostname = socket.gethostbyaddr(received.psrc)[0]
    except socket.herror:
        hostname = "Unknown"
    print(received.psrc + "\t\t" + hostname + "\t\t" + received.hwsrc)
