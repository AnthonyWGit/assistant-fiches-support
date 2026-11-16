# Besoin : assistant des fiches support

## Questions et réponses retenues
- Qui à accès aux fiches ? 
- *Les techniciens valident et ont accès aux fiches. Tous les techniciens ont accès. Pour générer les réponses, le service d'IA aussi*
- Lors d'une réponse, le technicien doit-il donner la fiche source ?
- *Oui, un technicien doit pouvoir se référer précisément à une fiche*
- Quelle forme de réponse ? 
- *Mot-clés si c'est pertinent, sinon texte complet*
- Format des fiches ? 
- *Markdown*
- Quelle(s) règle(s) pour la nomenclature ? 
- *kebab-case : **des-mots-separes-par-tiret-du-six***
- Accessibilité ? 
- *L'outil doit pouvoir être lu par un logiciel de lecteur d'écran*
- Temps de réponse maximum ? 
- *30 sec*
- Opération(s) interdite(s) ? 
- *Modifier et écraser les fiches*
- Taille maximum d'une fiche ? 
- *20 ko*
- Consommation de token ? 
- *Oui, à raison de 60000 token/session et 10 appels/session*
- Heures de service ? 
- *9h à 17h*
## Parcours
1. Le technicien reçoit un appel
2. Le technicien prend en charge l'appel
3. Le technicien reçoit une demande
4. Le technicien entre la demande dans l'assistant (outil en ligne de commande)
5. Le CLI transmet au service IA la demande
6. Le service d'ia formule une réponse en se basant sur une fiche déjà existante OU en crée une nouvelle
7. Le service d'ia fait passer la réponse au CLI
8. Le CLI reçoit la réponse et l'affiche dans le terminal
9. Le technicien peut répondre en s'appuyant sur des sources
## User story
- En tant que technicien helpdesk, je veux un outil en ligne de commande qui communique avec un service IA afin de formuler une réponse avec des sources
- En tant que technicien helpdesk, je veux un outil en ligne de commande qui communique avec un service IA pour pouvoir créer de nouvelles fiches
- En tant que CLI, je veux pouvoir recevoir une demande de la part du technicien helpdesk afin de pouvoir questionner le service IA 
- En tant que CLI, je veux pouvoir recevoir une réponse de la part du service IA afin de transmettre la réponse au technicien helpdesk
- En tant que service d'IA, je veux pouvoir recevoir et transmettre au CLI mes connaissances basées sur les fiches existantes
- En tant que CLI, je veux pouvoir recevoir des informations de la part du service IA et pouvoir créer des nouvelles fiches
## Critères d’acceptation
- Le format de la fiche techique est vérifié, son format est *markdown*, alors la demande est valide
- La nomenclature est respectée, elle est en kebab-case, alors la demande est valide
- Le CLI respecte des conventions d'accessibilité, par exemple supporte la lecture d'écran, alors l'assistant est accessible
- L'assistant répond rapidement quand la réponse met au max 30 sec pour venir alors le cachier des charges est respecté 
- Le service IA est en lecture seule, quand elle ne peut pas écraser ou modifier un fichier alors le cahier des charges est respecté
- Le poids d'une fiche est léger quand il est inférieur ou égal à 20ko alors la fiche est conservée
- Les appels au service IA sont limités quand on dispose de 60k token max par session, alors le technicien est averti
- La fiche technique existe déjà ; le technicien peut l'utiliser pour donner au client 
- La fiche technique n'existe pas ; le technicien fait appel au service d'IA pour en générer une nouvelle
## Objectifs d’accessibilité
- L'assisstant est conçu pour être utilisé lorsque le technicien est en situation de handicap
- Pas de message éphémère
- Des informations cruciales ne sont pas données par de la couleur
- Commande --help avec documentation