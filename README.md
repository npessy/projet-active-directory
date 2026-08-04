# Projet : Administrer Active Directory Domain Services

Ce projet guidé illustre, étape par étape, la mise en place et l'administration d'une infrastructure Active Directory complète sur AWS, de la préparation des serveurs jusqu'au durcissement de la sécurité. Le détail de chaque étape est disponible dans le sommaire ci-dessous.

## Infrastructure

Ce projet a été entièrement réalisé sur **AWS EC2 (Free Tier)**, en remplacement d'un environnement Hyper-V local, avec deux instances Windows Server 2025 :

| Instance | Rôle | Type |
|---|---|---|
| `AD-DC-01` | Contrôleur de domaine principal | t3.micro |
| `AD-MEMBER-01` | Second contrôleur de domaine / serveur membre | t3.micro |

**Domaine** : `tailwindtraders.internal`

## Contexte du projet

Ce projet s'appuie sur le [projet guidé Microsoft "Administrer les services de domaine Active Directory"](https://learn.microsoft.com/fr-fr/training/modules/guided-project-administer-active-directory-domain-services/).
## Sommaire du projet

### [01 — Préparation de l'infrastructure](./images/01_preparation/README.md)
Déploiement des instances EC2 sur AWS et configuration des Elastic IPs.

### [02 — Installation d'Active Directory Domain Services](./images/02_installation/README.md)
Installation du rôle AD DS et promotion en contrôleur de domaine.

### [03 — Configurer les opérations du contrôleur de domaine](./images/03_configurer_les_operations_du_controleur_de_domaine/README.md)
Promotion d'un second contrôleur de domaine, transfert du rôle FSMO, création d'un site et d'un sous-réseau.

### [04 — Configurer les opérations de gestion des utilisateurs](./images/04_configurer_les_opérations_de_gestion_des_utilisateurs/README.md)
Création d'unités d'organisation, gestion des utilisateurs et groupes, délégation de contrôle.

### [05 — Gérer les stratégies de mot de passe](./images/05_gerer_les_strategies_de_mot_de_passe/README.md)
Configuration de la stratégie de mot de passe du domaine, stratégie granulaire renforcée, activation de la corbeille Active Directory.

### [06 — Configurer les paramètres de sécurité](./images/06_configurer_les_parametres_de_securite/README.md)
Restriction de l'authentification NTLM, audit de la gestion des comptes, durcissement des droits utilisateurs.

## Compétences démontrées

- Administration Active Directory (utilisateurs, groupes, OU, GPO)
- Gestion de contrôleurs de domaine multiples et des rôles FSMO
- Configuration de stratégies de sécurité et de mots de passe
- Diagnostic et résolution de problèmes réseau et DNS via PowerShell (`nslookup`)
- Infrastructure cloud AWS (EC2, Elastic IP)
