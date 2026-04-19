# 🏢 Infrastructure & Administration Windows Server (Pasta Scaduta)

![Windows Server](https://img.shields.io/badge/Windows_Server-0078D6?style=for-the-badge&logo=windows&logoColor=white) ![Active Directory](https://img.shields.io/badge/Active_Directory-0078D6?style=for-the-badge&logo=microsoft&logoColor=white) ![Networking](https://img.shields.io/badge/Networking-VPN%20%7C%20DNS%20%7C%20DHCP-blue?style=for-the-badge) ![Security](https://img.shields.io/badge/Security-GPO%20%7C%20RODC-red?style=for-the-badge)

## 📝 Présentation du projet
[cite_start]Ce projet, réalisé dans le cadre du cursus MCSA Infrastructure Windows Server à SUPINFO, consiste en la conception et le déploiement d'une infrastructure informatique multi-sites complète pour une entreprise internationale (France, Pologne, Chine)[cite: 2730]. [cite_start]L'objectif est d'assurer une organisation robuste, sécurisée et hautement disponible[cite: 2732].

## 🌍 Topologie et Architecture Réseau
[cite_start]Le domaine principal `pasta-scaduta.lan` est réparti sur trois sites géographiques interconnectés via un **VPN site-à-site** (rôle RRAS) pour sécuriser les communications inter-serveurs et la réplication Active Directory[cite: 2820, 3087].

* [cite_start]🇫🇷 **Site France (Serveur Principal - 192.168.10.1)** [cite: 2740]
    * [cite_start]**Rôles cœurs** : Contrôleur de Domaine primaire (AD DS), DNS, DHCP (plage dynamique configurée)[cite: 2744, 2818].
    * [cite_start]**Stockage** : Déploiement d'un espace de noms **DFS** couplé à une cible **iSCSI**, reposant sur un volume **RAID 5** étendu pour optimiser la tolérance aux pannes et les performances de lecture[cite: 3200, 3203, 3227].
    * [cite_start]**Web** : Hébergement de l'intranet de l'entreprise via **IIS**[cite: 4023].

* [cite_start]🇵🇱 **Site Pologne (192.168.10.2)** [cite: 2858]
    * [cite_start]**Rôle** : Contrôleur de domaine avec **Catalogue Global (GC)** pour accélérer l'authentification et les recherches cross-sites des collaborateurs[cite: 2903, 2904].

* [cite_start]🇨🇳 **Site Chine (192.168.10.3)** [cite: 2927]
    * [cite_start]**Rôle** : Contrôleur de domaine en lecture seule (**RODC**) permettant de garantir la sécurité physique et logique des mots de passe sur un site distant et potentiellement moins sécurisé[cite: 2972, 2973].

## 🛡️ Stratégies de Groupe (GPO) et Sécurité
[cite_start]Afin de standardiser et sécuriser l'environnement de travail des différentes unités d'organisation (IT, HR, Marketing, Sales, Accounting), un ensemble rigoureux de GPOs a été déployé[cite: 3096]:

* [cite_start]**Sécurité des accès** : Politiques strictes de mots de passe (complexité, historique, durée de vie) avec des exigences distinctes pour le service IT et les utilisateurs standards[cite: 3559, 3636].
* [cite_start]**Restrictions système** : Verrouillage du poste de travail via la désactivation du Panneau de configuration et de l'Invite de commandes (CMD)[cite: 3398, 3476].
* [cite_start]**Déploiement logiciel** : Installation automatisée et silencieuse d'outils métiers (déploiement de paquets MSI pour 7-Zip et exécution de scripts pour Notepad++)[cite: 3297, 3330].
* [cite_start]**Environnement de travail** : Mappage automatique des lecteurs réseau par département (Drive Maps), verrouillage du fond d'écran d'entreprise et configuration imposée de la page d'accueil du navigateur[cite: 3742, 3848, 3942].

## 🤝 Fédération et Confiance
[cite_start]Mise en place d'une relation de confiance bidirectionnelle inter-forêts (Two-way Forest Trust) avec un domaine partenaire (`pastaammuffita.lan`) permettant l'authentification croisée et le partage de ressources[cite: 4068, 4103].

---
*Projet réalisé par Ahmadou DIALLO.*
