# Règles de gestion

Les règles de gestion de l'application de gestion agricole définissent les fonctionnalités et contraintes associées.

Attention, *les règles de gestion en italique* sont des suggestions et **ne sont pas prioritaires**.

## Gestion des terrains

- **RG1** : Un terrain possède un nom descriptif.
- **RG2** : Un terrain possède une surface exprimée en hectares ou en mètres carrés.
- **RG3** : Un utilisateur peut créer un terrain.
- **RG4** : Un utilisateur peut modifier un terrain.
- **RG5** : Un utilisateur peut supprimer un terrain.
- **RG6** : Lorsqu'un terrain est supprimé, tous les espaces de culture qui y sont associés sont supprimés.
- **RG7** : Un terrain peut contenir un ou plusieurs espaces de culture.

## Gestion des espaces de culture

- **RG8** : Un espace de culture possède un nom.
- **RG9** : Un espace de culture possède un type (rizière, champ, verger, potager).
- **RG10** : Un utilisateur peut créer un espace de culture.
- **RG11** : Un utilisateur peut modifier un espace de culture.
- **RG12** : Un utilisateur peut supprimer un espace de culture.
- **RG13** : Lors de la suppression d'un espace de culture, toutes les cultures et planches de culture associées sont supprimées.
- **RG14** : Un espace de culture peut contenir une ou plusieurs planches de culture.

## Gestion des planches de culture

- **RG15** : Une planche de culture possède un nom.
- **RG16** : Une planche de culture appartient à un espace de culture.
- **RG17** : Un utilisateur peut créer une planche de culture.
- **RG18** : Un utilisateur peut modifier une planche de culture.
- **RG19** : Un utilisateur peut supprimer une planche de culture.
- **RG20** : Lors de la suppression d'une planche de culture, toutes les cultures qui y sont associées sont supprimées.
- **RG21** : Une planche de culture peut contenir une ou plusieurs cultures.

## Gestion des cultures

- **RG22** : Une culture possède un nom.
- **RG23** : Une culture possède une variété.
- **RG24** : Une culture possède une date de plantation.
- **RG25** : Une culture peut être associée à un espace de culture ou à une planche de culture.
- **RG26** : Un utilisateur peut créer une culture.
- **RG27** : Un utilisateur peut modifier une culture.
- **RG28** : Un utilisateur peut supprimer une culture.
- **RG29** : Lors de la suppression d'une culture, toutes les actions associées à cette culture sont supprimées.
- **RG30** : Une culture possède un statut (en croissance, récoltée, malade, etc.).

## Gestion des actions agricoles

- **RG31** : Une action agricole possède un type (préparation du sol, plantation, entretien, protection, récolte).
- **RG32** : Une action agricole est associée à une date.
- **RG33** : Une action agricole peut contenir un commentaire.
- **RG34** : Un utilisateur peut créer une action agricole.
- **RG35** : Un utilisateur peut modifier une action agricole.
- **RG36** : Un utilisateur peut supprimer une action agricole.
- **RG37** : Une action agricole peut être associée à un espace de culture.
- **RG38** : Une action agricole peut être associée à une planche de culture.
- **RG39** : Une action agricole peut être associée à une culture précise.
- **RG40** : Un calendrier des actions est disponible pour chaque espace de culture.

## Gestion des observations et de la météo

- **RG41** : Un utilisateur peut enregistrer des observations sur un espace de culture.
- **RG42** : Une observation contient une date.
- **RG43** : Une observation contient une description.
- **RG44** : Une observation peut contenir des informations sur les conditions météo.
- **RG45** : Un utilisateur peut consulter l'historique des observations pour chaque espace de culture.

## Gestion des utilisateurs

- **RG46** : Chaque utilisateur possède un compte avec un identifiant et un mot de passe.
- **RG47** : Un utilisateur peut gérer uniquement ses propres terrains et espaces de culture.
- **RG48** : Un système de rôles permet de définir des permissions (propriétaire, collaborateur, visualisateur).
- **RG49** : Un administrateur peut inviter d'autres utilisateurs à collaborer sur un terrain.

## Notifications et rappels

- **RG50** : Un utilisateur peut activer ou désactiver les notifications.
- **RG51** : Un rappel automatique peut être configuré pour certaines actions agricoles.
- **RG52** : Les notifications peuvent être envoyées par e-mail ou via l'application mobile.

## Exportation et partage des données

- **RG53** : Un utilisateur peut exporter ses données sous format CSV ou PDF.
- **RG54** : Les données peuvent être partagées avec d'autres utilisateurs.

Cette liste peut être affinée en fonction des besoins spécifiques du projet.

