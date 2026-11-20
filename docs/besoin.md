# Besoin : assistant des fiches support

## Questions et réponses retenues
- Qui a accès aux fiches ? 
- *Les techniciens valident et ont accès aux fiches. Tous les techniciens ont accès. Pour générer les réponses, le service d'IA aussi.*
- Lors d'une réponse, le technicien doit-il donner la fiche source ?
- *Oui, un technicien doit pouvoir se référer précisément à une ou plusieurs fiches.*
- Quelle forme de réponse ? 
- *Mots-clés si c'est pertinent, sinon texte complet.*
- Format des fiches ? 
- *Markdown.*
- Quelle(s) règle(s) pour la nomenclature ? 
- *kebab-case : des-mots-separes-par-tiret-du-six*
- Accessibilité ? 
- *L'outil doit pouvoir être lu par un lecteur d'écran.*
- Temps de réponse maximum ? 
- *30 s.*
- Opération(s) interdite(s) ? 
- *Modifier et écraser les fiches.*
- Taille maximum d'une fiche ?
- *20 ko.*
- Consommation de jetons ? 
- *Oui, à raison de 60 000 jetons/session et 10 appels/session.*
- Heures de service ? 
- *9 h à 17 h.*
## Parcours
1. Le technicien reçoit un appel.
2. Le technicien prend en charge l'appel.
3. Le technicien reçoit une demande.
4. Le technicien entre la demande dans l'assistant (outil en ligne de commande).
5. Le CLI transmet la demande au service d'IA.
6. Le service d'IA formule une réponse en se basant sur une fiche déjà existante OU en crée une nouvelle.
7. Le service d'IA transmet la réponse au CLI.
8. Le CLI reçoit la réponse et l'affiche dans le terminal.
9. Le technicien peut répondre en s'appuyant sur des sources.
## User story
- En tant que technicien helpdesk, je veux un outil en ligne de commande qui communique avec un service d'IA afin de formuler une réponse avec des sources.
- En tant que technicien helpdesk, je veux un outil en ligne de commande qui communique avec un service d'IA pour pouvoir créer de nouvelles fiches.
- En tant que CLI, je veux pouvoir recevoir une demande de la part du technicien helpdesk afin de pouvoir questionner le service d'IA.
- En tant que CLI, je veux pouvoir recevoir une réponse de la part du service d'IA afin de transmettre la réponse au technicien helpdesk.
- En tant que service d'IA, je veux pouvoir recevoir et transmettre au CLI mes connaissances basées sur les fiches existantes.
- En tant que CLI, je veux pouvoir recevoir des informations de la part du service d'IA et pouvoir créer de nouvelles fiches.
## Critères d’acceptation
- Etant donné un technicien authentifié; quand il lance une commande ou écris un message alors il communique avec le service d'IA via le CLI en affichant un indicateur statique
- Etant donné un technicien authentifié, quand j'utilise le service il via CLI, alors il est dans la plage 9h-17h
- Etant donné un fichier, alors il est valide quand son poids est égal ou en dessous de 20 ko
- Etant donné que le technicien communique avec le service IA via CLI, quand il utilise le CLI, alors il a le droit à max 10 appels
- Etant donné une requête envoyée au service IA, quand cette dernière dure plus de 30 secondes, alors n'est pas valide et est refusée
- Etant donné une certaine nomenclature, quand les fiches sont lues ou écrites, alors ces fichiers sont nommés en kebab case
- Etant donné une requête, quand cette dernière essaie d'explorer hors du fichier de travail, alors elle est refusée
- Etant donné un technicien authentifié, quand celui-ci a des éléments secrets comme clé api, alors le fichier .env est jamais push et est couvert par gitignore
- Etant donné une consommation de jetons, quand celle-ci est égale à 60000 ou audessus, alors les requêtes sont refusées 
- Etant donné la création d'une nouvelle fiche, quand celle-ci est sur le point d'être écrasée alors il y a une demande de confirmation dans le terminal
- Etant donné une requête vide quand celle-ci ne contient rien ou que des espaces, alors il y a un retour de message d'erreur

## Objectifs d’accessibilité
- L'assistant est conçu pour être utilisé lorsqu'un technicien est en situation de handicap.
- Pas de messages éphémères.
- Les informations cruciales ne sont pas transmises uniquement par la couleur.
- Pas d'animations
- Commande --help avec documentation.