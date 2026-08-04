## Préparation de l'infrastructure

Afin de reproduire un environnement professionnel, j'ai déployé deux instances Windows Server 2025 sur AWS EC2 (Free Tier).

| Instance | Rôle | Type |
|---|---|---|
| `AD-DC-01` | Contrôleur de domaine principal | t3.micro |
| `AD-MEMBER-01` | Serveur membre | t3.micro |

Les deux instances sont déployées dans le même VPC, leur permettant de communiquer entre elles.

![Instances AWS](https://raw.githubusercontent.com/npessy/projet-active-directory/main/images/01_preparation/01_instances_aws.png)

Une Elastic IP a été associée à chaque instance afin de garantir une adresse IP publique fixe entre les sessions de travail.

![Elastic IP](https://raw.githubusercontent.com/npessy/projet-active-directory/main/images/01_preparation/02_elastic_ip.png)

---

[← Retour au sommaire principal](../../README.md) · [Étape suivante →](../02_installation/README.md)

