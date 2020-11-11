#Hostel Manager

Site de gestion de chambres d'un hôtel à mettre sur github en public

# API
l'api est disponible ici https://github.com/ydomenjoud/hostel-manager-api

mise en place :
```
git clone https://github.com/ydomenjoud/hostel-manager-api
cd hostel-manager-api
npm ci
npm start
```
api découvrable sur http://localhost:3000/explorer

# Client APP

## Gestion compte utilisateur

### Réaliser un composant *UserCredentialsComponent* qui représentera le formulaire de connexion et d'inscription :
  * prend en paramètre d'entrée le titre à afficher au dessus du formulaire et l'intitulé du bouton submit
  * affiche un formulaire avec deux champs : email et password ( en ReactiveForms )
    * l'email est requis et doit être au format email
    * le mot de passe est requis et doit faire 8 caractères minimum
  * le bouton submit doit être désactivé quand les champs sont invalides
  * lors du clic sur le bouton submit, le composant doit envoyer au composant parent un événement contenant le couple email/password

### Créer des pages et permettre de naviguer entre elle à travers une navigation en haut de page
  * inscription ( qui affiche le composant UserCredentialsComponent )
  * connexion  ( qui affiche le composant UserCredentialsComponent )
  * déconnexion ( qui affiche un bouton de confirmation )

### Gérer l'inscription/connexion utilisateur avec l'API à travers un Service
  * inscription ( description de l'API : http://localhost:3000/explorer/#!/users/users_create )
    * champs à envoyer à l'api : email, password
    * si l'inscription s'est bien passé, afficher le message "Votre inscription a bien été prise en compte" et cacher le formulaire
    * si l'inscription a rencontré une erreur, afficher le message d'erreur "Erreur dans l'inscription: " + suivi du message de l'erreur
  * connexion : ( description de l'API : http://localhost:3000/explorer/#!/users/users_login )
    * si la connexion est bonne, il faut rediriger vers la page d'accueil
    * si la connexion n'est pas bonne il faut afficher le message d'erreur
  * deconnexion : (description de l'API : http://localhost:3000/explorer/#!/users/users_logout )
    * si l'utilisateur clique sur oui, il faut le déconnecter ( api + local ) et rediriger vers la page d'accueil
    * si l'utilisateur clique sur non, il faut rediriger vers la page d'accueilx

## Dashboard

### Créer les squelettes des pages et permettre de naviguer entre elle à travers une navigation en haut de page ( compléter la précédente barre de navigation )
  * créer une chambre
  * liste des chambres
  * détail d'une chambre

### Gérer la liste des chambres et la création des chambres avec l'API à travers un Service
  * liste des chambres sous forme de table html: ( description de l'API : http://localhost:3000/explorer/#!/rooms/rooms_find )
    * => pour les lignes paires, le background des cellules doit être gris léger
    * => un bouton en fin de ligne permet d'accèder à la page de détail de la chambre ( avec l'id de la chambre en paramètre dans l'url )
  * créer une chambre: ( description de l'API: http://localhost:3000/explorer/#!/rooms/rooms_create ), champ name requis et minimum 5 caractères
  * détail d'une chambre: ( description de l'API: http://localhost:3000/explorer/#!/rooms/rooms_findById )

## Avancé

### Gérer l'accès ( Guard ) à certaines pages en fonction de l'état de la connexion
  * accès public : inscription / connexion
  * accès authentifié : créer une chambre / liste des chambre / déconnexion / profil

### Gestion du profil
  * page edition profil: affiche le composant UserCredentialsComponent et permettre de spécifier en plus son username et l'enregistrer dans l'API
    * => ( description de l'API : http://localhost:3000/explorer/#!/users/users_prototype_patchAttributes )
  * récupérer le profil utilisateur à la connexion, et afficher le username de l'utilisateur connecté en haut à droite de la navigation principale
   * => si le username n'a pas été renseigné, il faut afficher son "user " + son ID

### Gestion des éléments de la chambre, sur la page du détail de la chambre, permettre de :
  * donner la possibilité d'ajouter un objet dans la chambre ( description de l'API: http://localhost:3000/explorer/#!/rooms/rooms_prototype_create_items)
  * lister les objets dans la chambre ( description de l'API: http://localhost:3000/explorer/#!/rooms/rooms_prototype_get_items )
  * supprimer un objet dans la chambre (description de l'API: http://localhost:3000/explorer/#!/rooms/rooms_prototype_destroyById_items )

### Passer tous les composants en détection OnPush


### Gestion des formulaires
  * lorsque l'api renvoit une erreur concernant le champs email lors du login, il faut ajouter l'erreur sur le formcontrol de l'email
  * factoriser les pages Register, Login et Profil pour que la gestion des messages d'erreurs soit centralisée
  * factoriser les pages de détail et création d'une chambre

### Lazy loading
 * passer le module User en lazy loading
 * passer le module Room en lazy loading


### Directives
  * créer une directive qui met automatiquement ( sans modifier les pages actuelles, sans modifier le DOM ) une classe 'active' sur le lien actif
   ( comme routerLinkActive , mais sans avoir à le spécifier)
