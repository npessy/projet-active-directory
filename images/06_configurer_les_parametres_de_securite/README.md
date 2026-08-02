## Tâche 1 — Restreindre l'authentification NTLM

### 01 — Configuration de la restriction NTLM
Modification de la stratégie "Default Domain Controller Policy" via Group Policy Management. Le paramètre `Network security: Restrict NTLM: NTLM authentication in this domain` est configuré sur `Deny all`, interdisant l'utilisation du protocole d'authentification NTLM (jugé moins sécurisé que Kerberos) au sein du domaine `tailwindtraders.internal`.

![01_GPO_restrict_ntlm_deny_all](https://raw.githubusercontent.com/npessy/projet-active-directory/main/images/06_configurer_les_parametres_de_securite/01_tache/01_GPO_restrict_ntlm_deny_all.png)

---

## Tâche 2 — Auditer la gestion des comptes utilisateurs dans l'OU Sydney

### 02 — Création de la GPO SydneyOUPolicy
Création d'une nouvelle stratégie de groupe nommée `SydneyOUPolicy`, liée directement à l'unité d'organisation `Sydney`.

![02_GPO_sydneyoupolicy_creation](https://raw.githubusercontent.com/npessy/projet-active-directory/main/images/06_configurer_les_parametres_de_securite/02_tache/02_GPO_sydneyoupolicy_creation.png)

---

### 03 — Activation de l'audit de gestion des comptes
Configuration de l'audit `Audit User account management` (succès et échec) dans la stratégie `SydneyOUPolicy`, permettant de tracer toute création, modification ou suppression de compte utilisateur au sein de l'OU Sydney — une pratique essentielle de traçabilité et de conformité en sécurité Active Directory.

![03_GPO_audit_user_account_management](https://raw.githubusercontent.com/npessy/projet-active-directory/main/images/06_configurer_les_parametres_de_securite/02_tache/03_GPO_audit_user_account_management.png)

---

## Tâche 3 — Refuser l'ouverture de session en tant que service

### 04 — Configuration du refus "Log on as a service"
Configuration du paramètre `Deny Log on as a service` dans la stratégie `SydneyOUPolicy`, appliqué au groupe `Sydney Administrators`. Cette restriction empêche les comptes de ce groupe d'être utilisés pour démarrer des services Windows — une mesure de durcissement limitant la surface d'attaque en cas de compromission d'un compte administrateur.

![04_GPO_deny_logon_as_service_sydney_admins](https://raw.githubusercontent.com/npessy/projet-active-directory/main/images/06_configurer_les_parametres_de_securite/03_tache/04_GPO_deny_logon_as_service_sydney_admins.png)
