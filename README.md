Projet Windows Server – Pasta Scaduta

Contexte:
Projet réalisé dans le cadre du module MCSA Infrastructure Windows Server à SUPINFO.  
L’objectif était de mettre en place une infrastructure multi-sites pour l’entreprise fictive Pasta Scaduta, avec des serveurs en France, Pologne et Chine.

Le projet a été réalisé sur VMware, avec installation, configuration et documentation complète de l’environnement.


Architecture réseau
- Réseau LAN : 192.168.10.0/24  
- Serveurs déployés :
  - Server-France – 192.168.10.1  
  - Server-Pologne – 192.168.10.2  
  - Server-Chine – 192.168.10.3  
- DNS principal: 192.168.10.1 (Server-France)

---

Rôles et services configurés
Server-France
- DHCP, AD DS, DNS  
- Création de la forêt `pasta-scaduta.lan`  
- DFS, iSCSI et GPO (déploiement logiciel, restrictions, sécurité, mappage de lecteurs, wallpaper)  
- IIS (site web interne)

Server-Pologne
- Intégré au domaine principal  
- Catalogue Global activé  
- DFS et IIS configurés

Server-Chine
- Intégré au domaine en RODC (lecture seule)  
- DFS et IIS configurés


Résultats et tests
- Connexion inter-serveurs fonctionnelle  
- Réplication DFS validée  
- Site web IIS accessible depuis chaque serveur  
- Authentification Active Directory opérationnelle

