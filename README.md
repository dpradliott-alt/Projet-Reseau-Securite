
# Projet Réseau & Sécurité - Licence SDR

Ce dépôt regroupe quatre travaux pratiques réalisés dans le cadre de la formation de Master SDR (Sécurité des Données et des Réseaux). Chaque TP constitue une étape dans la construction d'une architecture réseau complète avec des services essentiels et sécurisés : firewall, messagerie, VPN.

## Objectifs généraux

* Mettre en place une infrastructure réseau réaliste sur environnement virtualisé (VirtualBox, KVM, etc.)
* Configurer des services réseau critiques : pare-feu, DNS, serveur mail, VPN
* Appliquer des mécanismes de sécurité : NAT, tunnel SSH, chiffrement TLS, VPN
* Manipuler les outils : pfSense, Postfix, Dovecot, OpenVPN, Wireshark

---

## Contenu du dépôt

```
|___ Captures                   #Captures d'écrans des 3 TPs
|___ TP1-PfSense
│   |__TP1-Pfsense.docx         # Rapport du TP2
│   |__TP1-Pfsense.md           # Version texte lisible / annotée
|__ TP2-Mail
│   |__ TP2-SERVEUR MAIL.pdf     # Rapport du TP3
│   |__ TP2-Mail.md              # Version texte lisible
|__ TP3-VPN
│   |__ TP3 OpenVPN terminé.pdf  # Rapport du TP4
│   |__ TP3-VPN.md               # Étapes + test tcpdump + schéma tunnel VPN
|__ README.md                   # Ce fichier
```

---

## Détail des TP

### TP1 - Configuration de pfSense (Firewall / NAT / DNS)

* Configuration LAN/WAN sur pfSense
* Définition des règles firewall entrantes/sortantes
* Mise en place de règles de NAT
* Test d'accès depuis LAN vers WAN

**Compétences :** NAT, Firewalling, sous-réseautage, filtrage IP, port forwarding

[Voir TP1](../TP1-Pfsense/TP1-Pfsense.md)

---

### TP2 - Serveur Mail (Postfix / Dovecot / GPG / IMAP)

* Installation d'un serveur mail local (Postfix en MTA, Dovecot en MDA)
* Configuration des boîtes locales pour utilisateurs (alice, bob)
* Accès IMAP via Thunderbird, test SMTP par Telnet
* Envoi chiffré de messages avec GPG
* Tunnel SSH + IMAP pour sécurisation externe

**Compétences :** Mails (MTA/MDA), IMAP/SMTP, alias utilisateurs, chiffrement GPG, tunnel SSH, Thunderbird

[Voir TP2](../TP2-Mail/TP1-Mail.md)


---

### TP3 - VPN avec pfSense et OpenVPN

* Mise en place d'un accès OpenVPN depuis l'extérieur (client .ovpn)
* Test du tunnel VPN depuis une machine physique (Windows)
* Analyse Wireshark (traçage du trafic chiffré)
* Détection active sur LAN via Wireshark

**Compétences :** VPN OpenVPN (mode client/server), export .ovpn, tcpdump, Wireshark, routage VPN

[Voir TP3](../TP3-VPN/TP3-VPN.md)


---

## Architecture virtuelle

* **pfSense** : routeur/firewall, LAN: `10.10.10.1`, WAN: `192.168.1.130`
* **Serveur Mail (Lubuntu)** : `10.10.10.10`, postfix + dovecot
* **Client interne (Kali)** : `10.10.10.50`
* **Client distant (Windows physique)** : accès via .ovpn, IP virtuelle : `192.168.200.2`

---

## Compétences mises en œuvre

* Configuration avancée de pfSense (NAT, Firewall, VPN)
* Installation et configuration d’un serveur mail complet
* Mécanismes de sécurité réseau : SSH, GPG, TLS, VPN
* Tests et dépannage avec telnet, openssl, mailutils, tcpdump, Wireshark
* Interconnexion réseau LAN/WAN simulée via pfSense

---

## Pour les recruteurs

Ces TP ont été réalisés de A à Z, incluant la résolution de problèmes réseau, l’analyse de flux, le durcissement de configurations, et le diagnostic sur interface CLI et GUI. Chaque projet a été documenté, testé et validé dans un environnement émulant un réseau d’entreprise.

Ce travail démontre une maîtrise de compétences techniques attendues en administration réseau / sécurité informatique.

