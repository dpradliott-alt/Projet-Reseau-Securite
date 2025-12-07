# Projet-Reseau-Securite
Ce dépôt regroupe quatre travaux pratiques. Chaque TP constitue une étape dans la construction d'une architecture réseau complète avec des services essentiels et sécurisés : firewall, messagerie, VPN.

Objectifs généraux

Mettre en place une infrastructure réseau réaliste sur environnement virtualisé (VirtualBox, KVM, etc.)
Configurer des services réseau critiques : pare-feu, DNS, serveur mail, VPN
Appliquer des mécanismes de sécurité : NAT, tunnel SSH, chiffrement TLS, VPN
Manipuler les outils : pfSense, Postfix, Dovecot, OpenVPN, Wireshark

Contenu du dépôt



Détail des TP

TP2 - Configuration de pfSense (Firewall / NAT / DNS)

Configuration LAN/WAN sur pfSense
Définition des règles firewall entrantes/sortantes
Mise en place de règles de NAT
Test d'accès depuis LAN vers WAN
Compétences : NAT, Firewalling, sous-réseautage, filtrage IP, port forwarding

TP3 - Serveur Mail (Postfix / Dovecot / GPG / IMAP)

Installation d'un serveur mail local (Postfix en MTA, Dovecot en MDA)
Configuration des boîtes locales pour utilisateurs (alice, bob)
Accès IMAP via Thunderbird, test SMTP par Telnet
Envoi chiffré de messages avec GPG
Tunnel SSH + IMAP pour sécurisation externe
Compétences : Mails (MTA/MDA), IMAP/SMTP, alias utilisateurs, chiffrement GPG, tunnel SSH, Thunderbird

TP4 - VPN avec pfSense et OpenVPN

Mise en place d'un accès OpenVPN depuis l'extérieur (client .ovpn)
Test du tunnel VPN depuis une machine physique (Windows)
Analyse Wireshark (traçage du trafic chiffré)
Détection active sur LAN via Wireshark
Compétences : VPN OpenVPN (mode client/server), export .ovpn, tcpdump, Wireshark, routage VPN

Architecture virtuelle

pfSense : routeur/firewall, LAN: 10.10.10.1, WAN: 192.168.1.130
Serveur Mail (Lubuntu) : 10.10.10.10, postfix + dovecot
Client interne (Kali) : 10.10.10.X
Client distant (Windows physique) : accès via .ovpn, IP virtuelle : 192.168.200.2

Compétences mises en œuvre

Configuration avancée de pfSense (NAT, Firewall, VPN)
Installation et configuration d’un serveur mail complet
Mécanismes de sécurité réseau : SSH, GPG, TLS, VPN
Tests et dépannage avec telnet, openssl, mailutils, tcpdump, Wireshark
Interconnexion réseau LAN/WAN simulée via pfSense

Pour les recruteurs

Ces TP ont été réalisés de A à Z, incluant la résolution de problèmes réseau, l’analyse de flux, le durcissement de configurations, et le diagnostic sur interface CLI et GUI. Chaque projet a été documenté, testé et validé dans un environnement émulant un réseau d’entreprise.
Ce travail démontre une maîtrise de compétences techniques attendues en administration réseau / sécurité informatique.
