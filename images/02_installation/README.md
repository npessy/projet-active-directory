# Installation AD DS sur AD-DC-01

* Installation du rôle Active Directory Domain Services
* Promotion en contrôleur de domaine
* Création du domaine tailwindtraders.internal
* 8 screenshots documentés

## Installation d'Active Directory Domain Services

### 01 — Installation du rôle AD DS
Installation du rôle Active Directory Domain Services via l'assistant "Add Roles and Features" de Server Manager. Le résultat montre "Installation succeeded" confirmant que le rôle AD DS est bien installé sur le serveur `EC2AMAZ-LJLP1AQ`.

![Installation rôle AD DS](https://raw.githubusercontent.com/npessy/projet-active-directory/main/images/02_installation/01_installation_role_ADDS.png)

---

### 02 — Deployment Configuration
Lancement de l'assistant de promotion du serveur en contrôleur de domaine. Sélection de l'option "Add a new forest" et saisie du nom de domaine racine `tailwindtraders.internal`.

![Deployment Configuration](https://raw.githubusercontent.com/npessy/projet-active-directory/main/images/02_installation/02_Add_NewForest.png)

---

### 03 — Domain Controller Options
Configuration des options du contrôleur de domaine : niveau fonctionnel Forest et Domain en Windows Server 2025, activation du serveur DNS et du Global Catalog. Définition du mot de passe DSRM (Directory Services Restore Mode).

![Domain Controller Options](https://raw.githubusercontent.com/npessy/projet-active-directory/main/images/02_installation/03_domain_controller_options.png)

---

### 04 — Additional Options
Vérification du nom NetBIOS assigné automatiquement au domaine : `TAILWINDTRADERS`.

![Additional Options](https://raw.githubusercontent.com/npessy/projet-active-directory/main/images/02_installation/04_additional_options.png)

---

### 05 — Paths
Confirmation des chemins de stockage par défaut pour la base de données AD DS, les fichiers journaux et le dossier SYSVOL :
- Database : `C:\Windows\NTDS`
- Log files : `C:\Windows\NTDS`
- SYSVOL : `C:\Windows\SYSVOL`

![Paths](https://raw.githubusercontent.com/npessy/projet-active-directory/main/images/02_installation/05_paths.png)

---

### 06 — Review Options
Récapitulatif complet de la configuration avant installation :
- Domaine : `tailwindtraders.internal`
- NetBIOS : `TAILWINDTRADERS`
- Forest Functional Level : Windows Server 2025
- Domain Functional Level : Windows Server 2025
- Global Catalog : Yes
- DNS Server : Yes

![Review Options](https://raw.githubusercontent.com/npessy/projet-active-directory/main/images/02_installation/06_review_options.png)

---

### 07 — Prerequisites Check
Vérification des prérequis : tous les contrôles sont passés avec succès ("All prerequisite checks passed successfully"). Des avertissements non bloquants sont affichés concernant la délégation DNS — normaux dans un environnement isolé AWS.

![Prerequisites Check](https://raw.githubusercontent.com/npessy/projet-active-directory/main/images/02_installation/07_prerequisites_check.png)

---

### 08 — Domaine créé
Confirmation post-redémarrage dans Server Manager que le domaine `tailwindtraders.internal` est bien actif et associé au serveur `EC2AMAZ-LJLP1AQ`.

![Domaine créé](https://raw.githubusercontent.com/npessy/projet-active-directory/main/images/02_installation/08_domaine_cree_tailwindtraders.png)

---

[← Retour au sommaire principal](../../README.md) · [Étape suivante →](../03_configurer_les_operations_du_controleur_de_domaine/README.md)
