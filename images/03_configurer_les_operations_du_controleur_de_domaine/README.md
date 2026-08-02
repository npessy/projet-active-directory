## Tâche 1 — Promouvoir AD-MEMBER-01 en second contrôleur de domaine

### 01 — Installation du rôle AD DS sur AD-MEMBER-01
Installation du rôle Active Directory Domain Services sur le serveur membre `EC2AMAZ-AQ1A4AT`. Le résultat montre "Installation succeeded" confirmant que le rôle AD DS est bien installé et prêt pour la promotion en second contrôleur de domaine.

![01_MEMBER_installation_role_ADDS](https://raw.githubusercontent.com/npessy/projet-active-directory/main/images/03_configurer_les_operations_du_controleur_de_domaine/01_Tache/01_MEMBER_installation_role_ADDS.png)

---

### 02 — Configuration DNS vers AD-DC-01
Configuration du serveur DNS sur `AD-MEMBER-01` via la commande PowerShell `Set-DnsClientServerAddress` pour pointer vers `AD-DC-01` (172.31.30.154). La commande `nslookup tailwindtraders.internal` confirme que le domaine est maintenant résolu correctement.

![02_MEMBER_dns_configuration](https://raw.githubusercontent.com/npessy/projet-active-directory/main/images/03_configurer_les_operations_du_controleur_de_domaine/01_Tache/02_MEMBER_dns_configuration.png)

---

### 03 — Configuration du UserPrincipalName de l'administrateur
Configuration du `UserPrincipalName` du compte Administrator sur `AD-DC-01` via PowerShell afin de permettre l'authentification lors de la jonction de `AD-MEMBER-01` au domaine. La commande `Get-ADUser` confirme que le UPN est bien défini : `Administrator@tailwindtraders.internal`.

![03_MEMBER_set_upn_administrator](https://raw.githubusercontent.com/npessy/projet-active-directory/main/images/03_configurer_les_operations_du_controleur_de_domaine/01_Tache/03_MEMBER_set_upn_administrator.png)

---

### 04 — Deployment Configuration — première tentative
Première tentative de configuration du déploiement avec le nom NetBIOS `TAILWINDTRADERS`. Cette tentative a échoué car le nom DNS complet `tailwindtraders.internal` est requis pour la jonction au domaine existant.

![04_MEMBER_deployment_configuration_tailwindtraders](https://raw.githubusercontent.com/npessy/projet-active-directory/main/images/03_configurer_les_operations_du_controleur_de_domaine/01_Tache/04_MEMBER_deployment_configuration_tailwindtraders.png)

---

### 05 — Deployment Configuration — configuration finale
Configuration finale du déploiement avec le nom DNS complet `tailwindtraders.internal` et les identifiants `Administrator@tailwindtraders.internal`. Cette configuration permet la promotion réussie de `AD-MEMBER-01` en second contrôleur de domaine.

![05_MEMBER_deployment_configuration_avec_credentials](https://raw.githubusercontent.com/npessy/projet-active-directory/main/images/03_configurer_les_operations_du_controleur_de_domaine/01_Tache/05_MEMBER_deployment_configuration_avec_credentials.png)

---

### 06 — Domain Controller Options
Configuration des options du second contrôleur de domaine : activation du serveur DNS et du Global Catalog (GC), désactivation du mode Read Only (RODC), et définition du mot de passe DSRM (Directory Services Restore Mode).

![06_MEMBER_domain_controller_options](https://raw.githubusercontent.com/npessy/projet-active-directory/main/images/03_configurer_les_operations_du_controleur_de_domaine/01_Tache/06_MEMBER_domain_controller_options.png)

---

### 07 — Prerequisites Check
Vérification des prérequis avant installation : tous les contrôles sont passés avec succès ("All prerequisite checks passed successfully"). Les avertissements en jaune concernant l'adresse IP statique et la délégation DNS sont non bloquants et normaux dans un environnement AWS.

![07_MEMBER_prerequisites_check](https://raw.githubusercontent.com/npessy/projet-active-directory/main/images/03_configurer_les_operations_du_controleur_de_domaine/01_Tache/07_MEMBER_prerequisites_check.png)

---

### 08 — Confirmation post-redémarrage
Confirmation dans Server Manager après redémarrage que `EC2AMAZ-AQ1A4AT` est bien membre du domaine `tailwindtraders.internal`, validant la promotion réussie en second contrôleur de domaine.

![08_MEMBER_post_reboot_domain](https://raw.githubusercontent.com/npessy/projet-active-directory/main/images/03_configurer_les_operations_du_controleur_de_domaine/01_Tache/08_MEMBER_post_reboot_domain.png)

---

## Tâche 2 — Transférer le rôle FSMO (RID Master)

### 09 — Operations Masters — avant transfert
Ouverture de la fenêtre "Operations Masters" depuis "Active Directory Users and Computers" sur `AD-MEMBER-01`. Le rôle RID Master est actuellement détenu par `EC2AMAZ-LJLP1AQ.tailwindtraders.internal` (AD-DC-01). Le transfert est initié vers `EC2AMAZ-AQ1A4AT.tailwindtraders.internal` (AD-MEMBER-01).

![09_FSMO_operations_masters](https://raw.githubusercontent.com/npessy/projet-active-directory/main/images/03_configurer_les_operations_du_controleur_de_domaine/02_Tache/09_FSMO_operations_masters.png)

---

### 10 — Confirmation du transfert
Fenêtre de confirmation du transfert du rôle RID Master. Le système demande une validation explicite avant d'effectuer l'opération, car le transfert d'un rôle FSMO est une action critique dans un environnement Active Directory.

![10_FSMO_confirmation_transfert](https://raw.githubusercontent.com/npessy/projet-active-directory/main/images/03_configurer_les_operations_du_controleur_de_domaine/02_Tache/10_FSMO_confirmation_transfert.png)

---

### 11 — Transfert réussi
Confirmation que le rôle RID Master a été transféré avec succès vers `EC2AMAZ-AQ1A4AT.tailwindtraders.internal` (AD-MEMBER-01). Le champ "Operations master" affiche désormais le nom du nouveau détenteur du rôle, confirmant que le transfert s'est effectué correctement.

![11_FSMO_transfert_reussi](https://raw.githubusercontent.com/npessy/projet-active-directory/main/images/03_configurer_les_operations_du_controleur_de_domaine/02_Tache/11_FSMO_transfert_reussi.png)

---

## Tâche 3 — Créer un site Active Directory et configurer un sous-réseau

### 12 — Création du site Sydney
Création d'un nouveau site Active Directory nommé `Sydney` depuis "Active Directory Sites and Services" sur `AD-DC-01`. Le site est associé au lien de site par défaut `DEFAULTIPSITELINK` avec le protocole de transport IP, permettant la réplication entre sites.

![12_AD_new_site_sydney](https://raw.githubusercontent.com/npessy/projet-active-directory/main/images/03_configurer_les_operations_du_controleur_de_domaine/03_Tache/12_AD_new_site_sydney.png)

---

### 13 — Confirmation de la création du site Sydney
Message de confirmation indiquant que le site `Sydney` a été créé avec succès. Le système indique les prochaines étapes recommandées : lier le site à d'autres sites, ajouter des sous-réseaux et installer des contrôleurs de domaine dans ce site.

![13_AD_site_sydney_confirme](https://raw.githubusercontent.com/npessy/projet-active-directory/main/images/03_configurer_les_operations_du_controleur_de_domaine/03_Tache/13_AD_site_sydney_confirme.png)

---

### 14 — Création du sous-réseau 172.16.1.0/24
Création d'un nouveau sous-réseau `172.16.1.0/24` dans le conteneur `tailwindtraders.internal/Configuration/Sites/Subnets`. Le sous-réseau est associé au site `Sydney`, permettant à Active Directory d'identifier les machines appartenant à ce site en fonction de leur adresse IP.

![14_AD_new_subnet](https://raw.githubusercontent.com/npessy/projet-active-directory/main/images/03_configurer_les_operations_du_controleur_de_domaine/03_Tache/14_AD_new_subnet.png)

---

### 15 — Configuration finale — site et sous-réseau
Vue finale de l'arborescence dans "Active Directory Sites and Services" confirmant la configuration complète :
- Site `Sydney` créé ✅
- Sous-réseau `172.16.1.0/24` associé au site Sydney ✅
- Site `Default-First-Site-Name` existant conservé ✅

![15_AD_subnet_cree](https://raw.githubusercontent.com/npessy/projet-active-directory/main/images/03_configurer_les_operations_du_controleur_de_domaine/03_Tache/15_AD_subnet_cree.png)
