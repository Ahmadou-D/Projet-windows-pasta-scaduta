# 🏢 Infrastructure Multi-Sites Windows Server (Pasta Scaduta)

![Windows Server](https://img.shields.io/badge/Windows_Server-0078D6?style=for-the-badge&logo=windows&logoColor=white) ![Active Directory](https://img.shields.io/badge/Active_Directory-0078D6?style=for-the-badge&logo=microsoft&logoColor=white) ![VMware](https://img.shields.io/badge/VMware-607078?style=for-the-badge&logo=vmware&logoColor=white)

## 📝 Contexte du projet
Ce projet a été réalisé dans le cadre du module **MCSA Infrastructure Windows Server** à SUPINFO. L'objectif principal était de concevoir, déployer et documenter une infrastructure informatique multi-sites sous VMware pour une entreprise fictive (Pasta Scaduta), avec des serveurs répartis géographiquement en France, en Pologne et en Chine.

## 🌍 Architecture Réseau
L'ensemble de l'infrastructure repose sur un réseau LAN défini en `192.168.10.0/24`, avec une résolution DNS centralisée sur le site français (`192.168.10.1`).

* **Server-France** : `192.168.10.1`
* **Server-Pologne** : `192.168.10.2`
* **Server-Chine** : `192.168.10.3`

## ⚙️ Rôles et Services Déployés

### 🇫🇷 Site France (Serveur Principal)
Cœur de l'infrastructure, ce serveur héberge les services critiques du domaine `pasta-scaduta.lan` :
* **Services d'infrastructure** : DHCP, DNS et contrôleur de domaine principal (AD DS).
* **Stockage et Partage** : Déploiement d'un espace de noms **DFS** et configuration **iSCSI**.
* **Sécurité et GPO** : Mise en place de stratégies de groupe avancées (déploiement de logiciels, restrictions système, règles de sécurité, mappage de lecteurs réseau, fond d'écran imposé).
* **Web** : Configuration d'un serveur **IIS** pour héberger le site web interne.

### 🇵🇱 Site Pologne
* Intégration au domaine principal en tant que contrôleur de domaine supplémentaire.
* Activation du **Catalogue Global** pour optimiser les requêtes et l'authentification.
* Configuration des services **DFS** (réplication) et **IIS**.

### 🇨🇳 Site Chine
* Intégration au domaine en tant que contrôleur de domaine en lecture seule (**RODC**), garantissant une sécurité accrue pour ce site distant.
* Configuration des services **DFS** et **IIS** locaux.

## 🚀 Résultats et Validation
L'environnement a été intégralement testé et validé sur VMware :
* Connexion inter-serveurs et routage fonctionnels.
* Réplication des données via DFS opérationnelle entre les sites.
* Site web intranet (IIS) accessible de manière transparente depuis chaque serveur.
* Authentification et réplication Active Directory validées sur l'ensemble de la forêt.

---
*Projet réalisé par Ahmadou DIALLO.*
