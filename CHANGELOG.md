# Journal du plugin himjlean

## 0.3.0 — 21 novembre 2026

- Skill `himjlean` 0.3.0 pour les organisations partagées : rôle Propriétaire, Admin ou Reader respecté, refus `forbidden_role` expliqué sans relance, équipe lue avant toute attribution, accord explicite avant une invitation, un changement de rôle ou un retrait, notifications résumées sans être marquées comme lues.
- Déclarations du serveur inchangées, en dehors de l’en-tête `X-Himjlean-Plugin-Version`.

## 0.2.0 — 16 novembre 2026

- Déclarations du serveur pour la production : `https://www.himjconception.com/mcp`, avec les applications OAuth de production de Codex, Claude Code et OpenCode. Les ports de retour ne changent pas.
- Skill inchangé.
- Les déclarations du serveur local de développement passent dans `examples/dev/`, que la marketplace n'installe pas.

## 0.1.0 — 15 novembre 2026

- Skill `himjlean` 0.1.0 : serveur himjlean seul, accord avant écriture, descriptions de tâches tirées du contexte, cadrage proposé sans être lancé, suggestions A, B, C pendant l’entretien, transmission des avis du serveur.
- Déclaration du serveur pour Codex (port 3116), Claude Code (port 3117) et OpenCode (port 3118), avec l’en-tête `X-Himjlean-Plugin-Version`.
