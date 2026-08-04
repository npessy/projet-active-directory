## Tâche 1 — Configurer la stratégie de mot de passe du domaine

### 01 — Modification de la stratégie de mot de passe par défaut
Modification de la stratégie "Default Domain Policy" via la console Group Policy Management. La longueur minimale du mot de passe est passée de la valeur par défaut à `14 caractères`, renforçant la sécurité des comptes du domaine `tailwindtraders.internal`.

![01_GPO_minimum_password_length](https://raw.githubusercontent.com/npessy/projet-active-directory/main/images/05_gerer_les_strategies_de_mot_de_passe/01_tache/01_GPO_minimum_password_length.png)

---

## Tâche 2 — Configurer une stratégie de mot de passe granulaire (Fine-Grained Password Policy)

### 02 — Création de la stratégie renforcée pour les administrateurs
Création d'une nouvelle stratégie de mot de passe granulaire nommée `Domain Admin Password Policy` depuis "Active Directory Administrative Center", avec une précédence de `1` et une longueur minimale de mot de passe de `16 caractères` — une exigence plus stricte que la stratégie par défaut du domaine.

![02_PSO_domain_admin_password_policy_creation](https://raw.githubusercontent.com/npessy/projet-active-directory/main/images/05_gerer_les_strategies_de_mot_de_passe/02_tache/02_PSO_domain_admin_password_policy_creation.png)

---

### 03 — Application de la stratégie au groupe Domain Admins
Application directe de la stratégie `Domain Admin Password Policy` au groupe `Domain Admins`, garantissant que les comptes à privilèges élevés respectent des exigences de mot de passe renforcées.

![03_PSO_directly_applies_to_domain_admins](https://raw.githubusercontent.com/npessy/projet-active-directory/main/images/05_gerer_les_strategies_de_mot_de_passe/02_tache/03_PSO_directly_applies_to_domain_admins.png)

---

## Tâche 3 — Activer la corbeille Active Directory (Recycle Bin)

### 04 — Activation de la corbeille Active Directory
Activation de la fonctionnalité "Recycle Bin" depuis "Active Directory Administrative Center", permettant la restauration d'objets Active Directory supprimés par erreur (utilisateurs, groupes, OU). Cette fonctionnalité, une fois activée, est irréversible.

![04_AD_recycle_bin_enabled](https://raw.githubusercontent.com/npessy/projet-active-directory/main/images/05_gerer_les_strategies_de_mot_de_passe/03_tache/04_AD_recycle_bin_enabled.png)

---

[← Retour au sommaire principal](../../README.md) · [Étape suivante →](../06_configurer_les_parametres_de_securite/README.md)
