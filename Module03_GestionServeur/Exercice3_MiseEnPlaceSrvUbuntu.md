# Exercice 3 - Installation d'un serveur Linux Ubuntu 20.04 Lts

Évaluation : formative
Durée estimée : 2 heures
Système d'exploitation : Ubuntu 20.04 serveur Lts

<b>Élément de compétence : </b>:

- Installation d'un serveur.(00Q1-2)
- Effectuer des tâches de gestion du système d'exploitation (00Q1-4)
- Rechercher des composants logiciels et matériels.(OOSF-2)

## Préparation de la machine virtuelle

- Sélectectionnez le dossier A21_4392_420244_ITV_JPD
- Créer une nouvelle machine virtuelle avec comme nom A21_4392_420W44_ITV_Ub_2004Srv_Matricule

- Donnez-lui les spécifications suivantes :
  -- CPU : 2
  -- Mémoire : 4 Go
  -- 3 nouveaux disques avec 10 Go, 20 Go e 20 Go sur SAN-DFC.  <a href="Images/Disque.png">Images ajout des disques</a>
  -- Fichier ISO : Synology-DFC -> ISO -> Ubuntu-20.04.2-live-serveur-amd64.iso
  -- Reseau : VM-DFC2
  Images de références : <a href="Images/ConfigVM.png">Image ConfigVM</a> , <a href="Images/ConfigVM.png">Fin de la config</a>.

## Consigne pour l'utilisation du clavier :

    - Vos déplacements doivent se faire avec la touche tabulation
    - La sélection d'une case à cocher ce fait avec la barre d'espacement.
    - La touche entrée vous permet d'entrer dans les listes déroulantes et de choisir une option. 

## Installation du serveur

- Choix de la langue : Fraçais  et Install Ubuntu.
- Disposition du Clavier : French(Canada) Variante canadien multilingue            
- Connexions réseau :  Fixe, réseau: 10.100.2.0/24, adresse ip: 10.100.2.[VotreÉcran], passerelle: 10.100.2.1, DNS :  199.202.105.108, 199.202.105.1 (voir les captures du cours théorique) 
- Adresse du proxy : laissez vide.
- Utilisez l'adresse de miroir proposée.    

### Préparation de l’espace disque

Cette section demande demande plusieurs manipulations, soyez prudent !

- Guided storage configuration
- Sélectionnez Custum storage layout  
- Commençons par créer une partition /boot sur un disque local hors du LVM.
- Sélectionez le disque dur (Sda) et ajouter une partition GPT.
- Ajoutez la taille 3 et le format (ext4), puis sélectionnez /boot comme point de montage.
- Enfin, sélectionnez Créer.
- Ensuite, créez les partitions standards swap de 4G.
- Laissez le reste 2.997  à une partition /tmp (sélectionnez Other et écrivez /tmp )

<b>Création du groupe de volume  (LVM)</b>

- Sélectionnez [Create volume gourp (LVM)]
- Nom du volume groupe : vg0 (valeur par défaut)
- Devices : cochez les disques (sdb, sdc), ce qui devrait donner Size : 39.992 G.
- Sélectionnez [créer]
- Dans la nouvelle fenêtre, DISQUES DISPONIBLES, sélectionnez vgo (new)...
- Sélectionnez create a logical volume
- Dans la nouvelle fenêtre changer le Name pour LV-Root avec une taille de 15G.
- Vous avez maintenant un premier volume logique sur monté sur / de 15G
- Faite la même chose pour créer des volumes logiques lv-home pour /home de /10G et le restes pour lv-var /var de 14.992 G.
- Toutes vos partitions sont maintenant créer vous pouvez sélectionnez [Terminé] et par la suite confirmer l'action.

Images de références : <a href="Images/PartitionFen1.png">Partitions</a> , <a href="Images/PartitionFen2.png">Partition deuxième fenêtre</a>.

### Configuration du profil

- Entrez votre nom

- Comme non de machine : <i>srvdevops_[VosInitiales]</i>

- Sélectionnez votre nom d'usager et votre mot de passe

- À la fenêtre suivante, installez OpenSSH server. 

- À la fenêtre Snap ne coché rien.

- Une fenêtre d'installation va apparaitre, elle dowlading and installing security updates.

- Quand ce sera terminé, vous pourez sélectionner sur [Redémarrez maintenant]
  
  <b>L'installation est terminée.<b>

 Lors de votre prière connexion, lisez l'ensemble des <a href="Images/Connexion
.png">informations</a>.
