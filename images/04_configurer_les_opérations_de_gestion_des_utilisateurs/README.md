## Tâche 1 — Créer les unités d'organisation (OU)

### 01 — Création de l'OU Sydney
Création d'une nouvelle unité d'organisation `Sydney` sous le domaine `tailwindtraders.internal`, depuis "Active Directory Users and Computers".

![01_OU_creation_sydney](https://raw.githubusercontent.com/npessy/projet-active-directory/main/images/04_configurer_les_opérations_de_gestion_des_utilisateurs/01_tache/01_OU_creation_sydney.png)

---

### 02 — Création de l'OU Melbourne
Création d'une seconde unité d'organisation `Melbourne` sous le même domaine, suivant la même procédure.

![02_OU_creation_melbourne](https://raw.githubusercontent.com/npessy/projet-active-directory/main/images/04_configurer_les_opérations_de_gestion_des_utilisateurs/01_tache/02_OU_creation_melbourne.png)

---

### 03 — Création de l'OU Brisbane
Création d'une troisième unité d'organisation `Brisbane`, complétant la structure organisationnelle du domaine.

![03_OU_creation_brisbane](https://raw.githubusercontent.com/npessy/projet-active-directory/main/images/04_configurer_les_opérations_de_gestion_des_utilisateurs/01_tache/03_OU_creation_brisbane.png)

---

### 04 — Arborescence finale des OU
Vue de l'arborescence dans "Active Directory Users and Computers" confirmant la création des trois unités d'organisation : `Sydney`, `Melbourne` et `Brisbane`.

![04_OU_arborescence_finale](https://raw.githubusercontent.com/npessy/projet-active-directory/main/images/04_configurer_les_opérations_de_gestion_des_utilisateurs/01_tache/04_OU_arborescence_finale.png)

---

## Tâche 2 — Créer l'utilisateur SydneyContractor

### 05 — Création de l'utilisateur SydneyContractor
Création d'un nouvel utilisateur `SydneyContractor` dans l'unité d'organisation `Sydney`, depuis "Active Directory Users and Computers".

![05_user_sydneycontractor_cree](https://raw.githubusercontent.com/npessy/projet-active-directory/main/images/04_configurer_les_opérations_de_gestion_des_utilisateurs/02_tache/05_user_sydneycontractor_cree.png)

---

### 06 — Configuration de la date d'expiration du compte
Configuration de la propriété `Account expires` dans l'onglet "Account" du compte `SydneyContractor`, afin de définir une date de fin de validité du compte.

![06_user_account_expiration](https://raw.githubusercontent.com/npessy/projet-active-directory/main/images/04_configurer_les_opérations_de_gestion_des_utilisateurs/02_tache/06_user_account_expiration.png)

---

### 07 — Création du groupe Sydney Administrators
Création d'un groupe de sécurité `Sydney Administrators` (portée Global) dans l'unité d'organisation `Sydney`.

![07_group_sydney_administrators_cree](https://raw.githubusercontent.com/npessy/projet-active-directory/main/images/04_configurer_les_opérations_de_gestion_des_utilisateurs/02_tache/07_group_sydney_administrators_cree.png)

---

### 08 — Ajout de SydneyContractor au groupe Sydney Administrators
Ajout du compte `SydneyContractor` au groupe `Sydney Administrators` via l'onglet "Member Of".

![08_user_membre_sydney_administrators](https://raw.githubusercontent.com/npessy/projet-active-directory/main/images/04_configurer_les_opérations_de_gestion_des_utilisateurs/02_tache/08_user_membre_sydney_administrators.png)

---

## Tâche 3 — Configurer SydneyContractor comme utilisateur protégé

### 09 — Ajout au groupe Protected Users
Ajout du compte `SydneyContractor` au groupe `Protected Users`, renforçant la sécurité du compte en interdisant l'utilisation de méthodes d'authentification faibles (NTLM, DES, RC4).

![09_user_protected_users](https://raw.githubusercontent.com/npessy/projet-active-directory/main/images/04_configurer_les_opérations_de_gestion_des_utilisateurs/03_tache/09_user_protected_users.png)

---

## Tâche 4 — Déléguer les droits de réinitialisation de mot de passe

### 10 — Sélection de la tâche à déléguer
Sélection de la tâche `Reset user passwords and force password change at next logon` dans l'assistant "Delegation of Control Wizard", pour le groupe `Sydney Administrators`.

![10_delegation_tasks_selection](https://raw.githubusercontent.com/npessy/projet-active-directory/main/images/04_configurer_les_opérations_de_gestion_des_utilisateurs/04_tache/10_delegation_tasks_selection.png)

---

### 11 — Confirmation de la délégation
Confirmation de la délégation de contrôle sur l'unité d'organisation `tailwindtraders.internal/Sydney`, accordée au groupe `Sydney Administrators` pour la réinitialisation des mots de passe.

![11_delegation_confirmation](https://raw.githubusercontent.com/npessy/projet-active-directory/main/images/04_configurer_les_opérations_de_gestion_des_utilisateurs/04_tache/11_delegation_confirmation.png)

---

[← Retour au sommaire principal](../../README.md) · [Étape suivante →](../05_gerer_les_strategies_de_mot_de_passe/README.md)
