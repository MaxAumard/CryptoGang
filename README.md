# CryptoGang

 * **Sujet 2** ;
 * **Difficulté : Assez Difficile** ;
 * **Titre : Quizz**.

## Rudiments cryptographiques

  * Questions **chiffrées** & stockées dans un fichier quizz.dat ;
  * keystore : `keystore.ks` :
    * format : `JCEKS` ;
    * contient : clés permettant de déchiffrer les questions ;
    * Chiffrement pour les questions : `AES` en mode `CBC` avec le rembourrage `PKCS5Padding`.

## Le Quizz

  * Une question est posée :
    * Si la réponse est fausse, la question est reposée ;
    * Si la réponse est correcte, alors il passe à la question suivante[^1].
    
## Attaque(s)
> Le fait de pouvoir accéder **à une entrée** du `keystore` via le MdP généré constitue le seul et unique moyen pour l'aaplication de déterminer si le joueur a répondu
correctement à la question et d'afficher la question suivante. $\implies$ Si le joueur ne connaît pas la réponse il peut tenter un `brut force`.

Pour éviter cela, il faut générer les mots de passe protégeant les entrées du keystore via une méthode garantissant une certaine protection contre ce type d'attaques.

## Améliorations

  * Première question du quizz random : au lieu de commencer le quizz à la question `id=1`, on peut commencer, *par exemple* : par la question `id=5`. Les questions d'après
  seraient, dans cet ordre, `id=6`, `id=7`, `...` ;
  * Aléatoire complet dans les questions : on commence avec la question `id=3`, puis la `7`, puis la `2`, etc ;
  * Réaliser une IHM (via une page web par exemple).
  
## Todo

- [ ] Créer le fichier `quizz.dat` ;
- [ ] Créer une batterie de questions pour le quizz ;
- [ ] Insérer les questions chiffrées dans le fichier `quizz.dat`
- [ ] Créer le keystore ;
- [ ] Mettre les clés permmenttant de déchiffrer les questions dans le `keystore` ;
- [ ] Créer la vérification des réponses (correctes ou fausses) ;
- [ ] Après déchiffrement de la question, la ranger dans une instance du type `String` ;
- [ ] Protéger contre le `brut force` ;
- [ ] Gestion des erreurs.

[^1]: Le mot de passe protégeant l'entrée du `keystore` qui contient la clé ayant servi à chiffrer cette question est généré à partir de la bonne réponse à la question précédente.
