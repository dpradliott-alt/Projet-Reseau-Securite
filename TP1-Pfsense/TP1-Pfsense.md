# TP1 - Configuration de pfSense

## Objectif

Mettre en place un routeur pfSense fonctionnel dans un réseau local avec plusieurs interfaces réseaux, une interface d'administration, un LAN, et une machine cliente Kali pour tester la connectivité et les règles de pare-feu.

_**TP réalisé avec Proxmox 8.4.0**_

---

## Infrastructure mise en place


![Topologie](../captures/TP1/TopologieTP1.PNG)



* **lubuntu** (serveur apache2 / futur serveur mail)

  * LAN : 10.10.10.10/24
  * Gateway : 10.10.10.1/24


* **pfSense** (routeur virtuel)

  * WAN : 192.168.1.130/24 (connecté à mon réseau domestique)
  * LAN : 10.10.10.1/24

* **Client Kali** (connecté sur LAN pfSense)

  * Adresse IP : 10.10.10.50/24
  * Gateway : 10.10.10.1

* **Interface Web de pfSense**

  * Accessible depuis Kali via : http://10.10.10.1
  * Ou depuis mon réseau domestique en 192.168.1.130
 
  ![Interfaces WAN/LAN](../captures/TP1/InterfacesPf.JPG)

## Configuration initiale de pfSense

* Assignation des interfaces WAN (vtnet0) et LAN (vtnet1)
* Attribution manuelle des IP
* Désactivation du DHCP sur WAN
* Activation du DHCP sur LAN
* Configuration du DNS et du domain cs.cr
* IP statique pour le lubuntu 10.10.10.10
* Test de ping entre pfSense → Kali et Kali → pfSense

![configuration](../captures/TP1/dashboard.JPG)


## Configuration des règles de pare-feu

### Règles WAN

* Autorisation des connexions entrantes sur HTTP/HTTPS depuis le réseau domestique


![FirewallWan](../captures/TP1/rulesWAN.JPG)

### Règles LAN

* Accès total sortant depuis LAN (par défaut)

![Firewalllan](../captures/TP1/rulesLAN.JPG)

## Test de connectivité

Depuis Kali (10.10.10.50) :

* Accès à l'interface web de pfSense : OK
* Ping vers 192.168.1.33 (réseau domestique) : OK

Depuis lubuntu (10.10.10.10) :

* Accès à l'interface web de pfSense : OK
* Ping vers 192.168.1.33 : OK

Depuis réseau domestique (192.168.1.33) :

* Accès à l'interface web : OK
* Ping vers LAN : OK


## Conclusion

TP1 posait les bases : installation, réseaux LAN/WAN, règles de pare-feu, et connectivité entre Kali et le monde extérieur via pfSense. C'est le socle pour les TP suivants sur le mail (TP2) et le VPN (TP3).

