# TP OpenVPN sur pfSense 

*Ce document décrit la mise en place d’un tunnel VPN OpenVPN sécurisé sur pfSense. L’objectif est de permettre à un client distant (sous Windows) d’accéder à un réseau local (LAN) protégé, via un tunnel chiffré traversant Internet, en utilisant pfSense comme serveur VPN.*

--

## Objectif

Mettre en place un VPN **OpenVPN** sur pfSense afin de fournir un accès distant sécurisé au LAN. Le but est qu’un utilisateur externe (par exemple sur un PC Windows connecté depuis Internet) puisse accéder aux ressources internes du réseau local **comme s’il était sur site**, tout en garantissant **confidentialité** et **authentification**. Le tunnel VPN chiffré permettra de traverser Internet de manière sûre, protégeant ainsi le LAN des accès non autorisés et des interceptions de trafic. Ce TP vise donc à configurer OpenVPN sur pfSense et à vérifier qu’un client distant peut se connecter au travers d’une connexion sécurisée (certificats + identifiants) pour atteindre le LAN protégé.

--

## Infrastructure

L’infrastructure de test se compose d’un routeur/pare-feu **pfSense** et de deux réseaux : le réseau **WAN** (côté Internet) et le réseau **LAN** interne. Le **pfSense** possède une interface WAN (connectée à Internet ) et une interface LAN connectée au réseau local **10.10.10.0/24**. Le serveur OpenVPN sera hébergé sur pfSense et utilisera un **réseau de tunnel VPN** dédié (`192.168.200.0/24`) pour attribuer des adresses IP virtuelles aux clients VPN.

Une machine cliente **Windows** située à l’extérieur (sur Internet) sera configurée pour se connecter au VPN. Lors de la connexion, pfSense attribuera au client une adresse IP dans le réseau du tunnel (par exemple **192.168.200.2**), lui permettant de communiquer avec le LAN interne **10.10.10.0/24**.

--

## Configuration sur pfSense

1. Création de l'autorité de certification (CA)
2. Génération des certificats serveur et client
3. Création d'un utilisateur VPN avec certificat
4. Assistant de configuration OpenVPN :

   * Mode Remote Access (SSL/TLS + User Auth)
   * Tunnel Network : 192.168.200.0/24
   * Local Network : 10.10.10.0/24
   * Port : UDP 1194
   * DNS : 10.10.10.1 
5. Création automatique des règles firewall via l'assistant

--

## Export du client VPN

* Installation du paquet openvpn-client-export
* Export du fichier .ovpn pour l'utilisateur alice
* Format : Inline configuration incluant certificat, clé, CA

--

## Connexion depuis le client Windows

* Installation d'OpenVPN Connect ou GUI
* Importation du fichier .ovpn
* Connexion avec identifiants alice
* Attribution d'une IP tunnel (ex : 192.168.200.2)

--

## Tests de connectivité

* `ipconfig` : vérifier IP VPN attribuée
* `ping 10.10.10.10` : test de communication avec le LAN
* Wireshark : observer trafic UDP 1194 chiffré uniquement

--

## Sécurité

* Authentification forte (certificat + login/password)
* Chiffrement TLS + AES-256-GCM
* Preuve de chiffrement via Wireshark sur WAN

--

## Conclusion

Le TP met en place un accès distant sécurisé via VPN. Le client Windows accède aux ressources internes du LAN à travers un tunnel chiffré, sans exposer directement les services internes. OpenVPN sur pfSense permet ainsi une solution sûre pour le télétravail ou l'administration à distance.

