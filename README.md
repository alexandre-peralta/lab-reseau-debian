Laboratoire Réseau Debian 13

Infrastructure réseau complète sous Debian 13 (trixie), entièrement en ligne de commande, montée sur VMware Fusion dans un réseau local isolé 192.168.10.0/24.

Objectif

Monter et documenter une petite infrastructure réseau d'entreprise avec les services de base: un routeur Debian relié à Internet, puis les serveurs DHCP, DNS, FTP, SSH et web, testés depuis un client.

Architecture

	•	RTR-DEB, 192.168.10.1: routeur avec routage IPv4 et NAT nftables, une carte vers Internet et une carte vers le LAN isolé
	•	SRV-DHCP, 192.168.10.2: serveur DHCP (isc-dhcp-server), plage 192.168.10.100 à 192.168.10.200
	•	SRV-DNS, 192.168.10.3: serveur DNS (bind9), domaine farol.lan, zone directe et zone inverse, forwarder vers l'extérieur
	•	SRV-FTP, 192.168.10.4: serveur FTP (vsftpd) avec accès par utilisateur
	•	SRV-SSH, 192.168.10.5: serveur SSH (openssh-server), connexion par mot de passe puis par clés ed25519
	•	SRV-WEB, 192.168.10.6: serveur web (Apache2)
	•	CLIENT-DEB: client avec interface graphique, qui reçoit son adresse par DHCP et résout les noms par le DNS

Méthode

Une VM de base préparée une seule fois (dépôts, mises à jour, shell configuré), puis un clone complet pour chaque machine. Chaque serveur suit les mêmes étapes: création du clone et nom d'hôte, installation du service avec accès Internet, puis bascule sur le réseau isolé avec adresse fixe.

Compétences démontrées

Administration Debian en ligne de commande, routage et NAT, configuration réseau, DHCP, DNS, FTP, SSH et authentification par clés, Apache, clonage de VM, tests et dépannage.

Difficultés rencontrées

Dépôts pointant encore sur le DVD d'installation, et SSH absent des clones, résolus dans la documentation.

Documentation

Le PDF complet avec toutes les étapes et les captures d'écran se trouve dans ce repository.