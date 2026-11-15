---
name: himjlean
description: Utiliser le serveur MCP himjlean pour lire et gérer les projets, les tâches et le cadrage stratégique d’une personne sur himjlean (HIMJ Conception). À utiliser dès qu’elle parle de ses tâches, de son projet himjlean, d’en créer ou d’en modifier une, ou de son cadrage stratégique.
---

# himjlean

himjlean range les projets d’une personne, leurs tâches et leur cadrage stratégique. Le serveur MCP `himjlean` donne accès à ces données. Ce skill dit comment préparer chaque appel. Les règles de fond (droits, verrouillage, versions) sont appliquées par le serveur.

## Toujours passer par himjlean

- Pour tout ce qui concerne himjlean, appeler uniquement les outils du serveur `himjlean` (leur nom commence par `himjlean_`).
- Ne jamais se rabattre sur un outil au nom proche d’un autre serveur, par exemple `get_project` de Linear. Si les outils himjlean sont absents de la session, le dire à la personne et lui proposer de vérifier la connexion MCP, puis d’ouvrir une nouvelle conversation.
- Quand le projet n’est pas clair, le demander ou le choisir avec `himjlean_select_project`. Quand une réponse contient `in_project`, nommer ce projet à la personne.

## Demander l’accord avant d’écrire

Créer, modifier, changer l’état ou supprimer une tâche, ou enregistrer une réponse de cadrage, demande l’accord de la personne. Exception : elle l’a demandé explicitement dans son message (« crée la tâche… », « passe-la en cours »). `confirmed_by_human` ne se pose qu’après son accord explicite.

## Écrire des descriptions de tâches utiles

Avant `himjlean_create_task` ou `himjlean_update_task`, rassembler ce que la conversation et le dépôt ouvert disent de la tâche : fichiers concernés, décision prise, problème observé. Écrire une description courte (500 caractères au plus) qui dit :

1. ce qu’il faut faire, avec les éléments concrets (écran, fichier, comportement) ;
2. pourquoi, si la raison est connue ;
3. à quoi on reconnaît que c’est terminé.

Ne rien inventer : une information absente du contexte n’entre pas dans la description. Sans contexte utile, laisser la description vide plutôt que de reformuler le titre. Avant de créer, vérifier les doublons avec `himjlean_find_similar_tasks` et les signaler.

## Cadrage stratégique

- Quand un projet n’a pas de cadrage, le proposer une fois, sans jamais lancer l’entretien seul.
- Pendant l’entretien lancé avec `himjlean_start_cadrage`, suivre le protocole renvoyé par le serveur. Sous chaque question, proposer trois réponses possibles, A, B et C, tirées de ce que l’on sait de la personne et de son projet, puis laisser une réponse libre. Les présenter comme des suggestions, jamais comme la réponse retenue.
- N’envoyer à `himjlean_save_cadrage_answers` que la réponse choisie ou écrite par la personne.

## Avis du serveur

Une réponse d’outil peut se terminer par un « Avis himjlean pour la personne ». Le transmettre en une phrase, avec la commande de mise à jour s’il y en a une, puis reprendre la tâche en cours. Lancer la commande seulement avec l’accord de la personne. Après un avis de nouveaux outils, proposer d’ouvrir une nouvelle conversation pour les voir.
