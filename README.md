# Projet Final - Utilisateur eductive16

Le projet consistait à deployer une infrastructure avec l'aide de Terraform sur OVH, puis ansible mais aussi la technologie docker.

## Mise en place

Il faut installer terraform et ansible et créer un workspace pour terraform et sourcer ses credentials.
```
apt-get install terraform
apt-get install ansible
cd terraform/
terraform workspace new tp_final_terraform
terraform workspace select tp_final_terraform
```

Ensuite vérifier le fichier providers.tf, puis:
```
source ~/openrc.sh
```

## Lancer les différentes instances

```
terraform plan
terraform apply
```

Entrer "yes" pour approuver et vous pourez vérifer l'installation de tout cela en faisant:
```
terraform show
```

## Provisioner les intances grâce à Ansible 

Aller dans le dossier Ansible:
```
cd ../ansible/

```

Puis lancer la commande suivante, afin de provisioner les instances via le deploy-infra.yml:
```
ansible-playbook tp-deployinfra.yml -i inventory.yml --ssh-common-args='-o StrictHostKeyChecking=no

```

### Effectuer les tests des backends depuis le front

Tout d'abord, vous devez recuperer l'IP publique du front grâce à la commande: ``` terraform show ```

Vous trouverez sur les backends 1, qui seront sur le port 80, une page web qui affichera un chat en image qui elle change au fur et à mesure que vous rechargez la page, avec une phrase contenant le meilleur utilisateur, qui est le notre.

    Disponible ici:  (adresse ip publique):80

Vous trouverez sur les backends 2, qui seront sur le port 81, une page web qui affichera un tableau aves des informations sur nos informations d'adresses IPs. 

    Disponible ici:  (adresse ip publique):81

Vous trouverez sur les backends 3, qui seront sur le port 82, une page web qui affichera tout simplement un wordpress.

    Disponible ici:  (adresse ip publique):82