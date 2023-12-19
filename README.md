# Paquet-sur-Ansible
# Comment déployer des paquets via Ansible 

--En tout premier lieu, faire une reservation IP sur https://gipens.ens-lyon.fr/, la machine prendra le suffix DNS du vlan en question--
![image](https://github.com/BilobiloIT/Paquet-sur-Ansible/assets/118860544/2cbcd1cf-3df3-4d01-b906-8f5efe4f982d)


--Ne pas oublier de passer la configuration réseau en manuel sur la machine--


(Installer open-ssh sur la machine [sudo apt-get install openssh-serveur]
1ère étape : Mettre la clé publique SSH d'Ansible sur la machine dans /root/.ssh/authorized_keys, trouvable sur le serveur lxc-ansible dans /etc/ansible/ssh-key/ansible.pub.


2ème étape : Faire
