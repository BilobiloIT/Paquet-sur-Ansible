# Paquet-sur-Ansible
# Comment déployer des paquets via Ansible 

--En tout premier lieu, faire une reservation IP sur https://gipens.ens-lyon.fr/, la machine prendra le suffix DNS du vlan en question--
![image](https://github.com/BilobiloIT/Paquet-sur-Ansible/assets/118860544/2cbcd1cf-3df3-4d01-b906-8f5efe4f982d)


--Ne pas oublier de passer la configuration réseau en manuel sur la machine--


(Installer open-ssh sur la machine [sudo apt-get install openssh-serveur]
1ère étape : Mettre la clé publique SSH d'Ansible sur la machine dans /root/.ssh/authorized_keys, trouvable sur le serveur lxc-ansible dans /etc/ansible/ssh-key/ansible.pub.


2ème étape : Intégrer la machine dans le serveur grâce au script ./ansible/maintenance.sh host [Nom_De_La_Machine] et choisir le groupe dans lequelle on mets la machine


3ème étape : Aller dans /etc/ansible/hosts, pour que cela fonctionne, la machine doit être renseignée sous le format [Nom_De_La_Machine].[Dns] :  ![image](https://github.com/BilobiloIT/Paquet-sur-Ansible/assets/118860544/0ac3bf7b-a9f9-42ba-908a-cf37209f5007)*
*Il n'y a pas besoin de renseigner .dsi.ens-lyon.fr

