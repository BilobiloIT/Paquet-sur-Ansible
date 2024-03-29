### Paquet-sur-Ansible
## Comment déployer des paquets via Ansible 

--En tout premier lieu, faire une reservation IP sur https://gipens.ens-lyon.fr/, la machine prendra le suffix DNS du vlan en question--
![image](https://github.com/BilobiloIT/Paquet-sur-Ansible/assets/118860544/67c39c3a-0f19-4e2d-a7f0-4e36aefcc786)



--Ne pas oublier de passer la configuration réseau en manuel sur la machine--


(Installer open-ssh sur la machine *sudo apt-get install openssh-serveur*


## 1ère étape : Mettre la clé publique SSH d'Ansible sur la machine dans /root/.ssh/authorized_keys, trouvable sur le serveur lxc-ansible dans /etc/ansible/ssh-key/ansible.pub.


## 2ème étape : Intégrer la machine dans le serveur grâce au script `./ansible/maintenance.sh host [Nom_De_La_Machine]` et choisir le groupe dans lequelle on mets la machine


## 3ème étape : Aller dans /etc/ansible/hosts, la machine doit être renseignée sous le format [Nom_De_La_Machine].[Dns] :  ![image](https://github.com/BilobiloIT/Paquet-sur-Ansible/assets/118860544/0ac3bf7b-a9f9-42ba-908a-cf37209f5007)*

*Il n'y a pas besoin de renseigner .dsi.ens-lyon.fr

### Après toutes ces étapes essayer de ping la machine et de nslookup pour voir si tout fonctionne

## 4ème étape : La création du paquet à déployer, pour cette exemple j'ai utilisé le paquet calendrier connu sous le nom ***Calendar***
`Il existe des formats déjà présent, je penses qu'il faut les respecter` : [NomDuService-NomDuPaquet] * : ![image](https://github.com/BilobiloIT/Paquet-sur-Ansible/assets/118860544/b21abd62-5330-4e7d-b6c3-4a3c32520ee3)

 - Aller dans /etc/ansible/roles : Mettre un nom de dossier

    > Pour mon paquet Calendrier, j'ai choisi le nom SGP-calendar
    
    Crée un dossier files* et un dossier task*

   
<sup>*le dossier files correspond à des fichiers à copier sur les hôtes, il n'est pas nécessaire qu'il contienne quelque chose</sup>

<sup>*le dossier tasks doit contenir les tâches à exécuter </sup>

Une fois le dossier tasks crée, la création d'un fichier texte `main.yml` est nécessaire, ce sera ce fichier qui sera exécuté* lors du déclenchement de la tâche

<sub>*par défaut </sub>

Pour mon exemple, le module* que j'ai utilisé est apt, donc mon fichier `main.yml` ressemble à :  ![image](https://github.com/BilobiloIT/Paquet-sur-Ansible/assets/118860544/a3210d3a-daf4-4824-b1b8-f22ee2fff10e)

<sub>*Les modules sont file, copy, apt, service, command, shell, cron</sub>

## 5ème étape : Déploiement du paquet de manière manuel 
Pour lancer un déploiement de manière manuel il faudra renseigner un autre fichier en yaml.
 - Aller dans /etc/ansible/playbooks/manuel
 - Crée un fichier texte
 - Renseigner de la même manière le fichier que dans `/etc/ansible/playbooks/SGP.yml` : ![image](https://github.com/BilobiloIT/Paquet-sur-Ansible/assets/118860544/44c69406-2f77-430a-951a-324215c2db69)

 
 - , rajouter en commentaire dans la première ligne la commande complète qui est *ansible-playbook [CheminVerssLeFichier.yml]*


Donc pour mon calendar : ![image](https://github.com/BilobiloIT/Paquet-sur-Ansible/assets/118860544/a2e52113-b41b-45d6-9fe2-73f7e26e9b88)

puis je lance la ligne de commande *ansible-playbook /etc/ansible/playbooks/manuel/calendartest.yml*






