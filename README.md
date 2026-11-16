# Plugin himjlean

> **Bêta.** Les déclarations visent le serveur himjlean de production, `https://www.himjconception.com/mcp`. Il faut un compte himjlean pour autoriser la connexion.

Le plugin himjlean réunit le skill `himjlean` et la déclaration du serveur MCP himjlean pour Codex, Claude Code et OpenCode. Le serveur est hébergé : ses outils évoluent sans mise à jour du plugin.

## Identifiants d'application

Les trois applications OAuth déclarées ici (une par client) sont des clients publics, sans secret. Un agent installé sur la machine de quelqu'un ne peut rien garder de confidentiel : le même plugin est distribué à tout le monde, donc un secret qui s'y trouverait n'en serait plus un. La protection vient d'ailleurs : la vérification PKCE de la connexion, les adresses de retour limitées au poste local (ports 3116 à 3118), et l'écran de consentement himjlean qui affiche le compte connecté avant d'autoriser.

## Installer

Codex :

```sh
codex plugin marketplace add himj69/himjlean-plugin
codex plugin add himjlean@himjlean
codex mcp login himjlean
```

Claude Code :

```sh
claude plugin marketplace add himj69/himjlean-plugin
claude plugin install himjlean@himjlean
```

Puis, dans une session terminale, `/mcp`, le serveur himjlean, **Authenticate**.

OpenCode : copier le bloc de [opencode/opencode.json](opencode/opencode.json) dans son `opencode.json`, puis :

```sh
npx skills add himj69/himjlean-plugin --skill himjlean
opencode mcp auth himjlean
```

## Mettre à jour

Une seule commande met à jour le skill et la déclaration. Le serveur prévient quand une version est disponible.

| Client | Commande | Ensuite |
| --- | --- | --- |
| Codex | `codex plugin marketplace upgrade himjlean && codex plugin add himjlean@himjlean` | Ouvrir une nouvelle conversation |
| Claude Code | `claude plugin marketplace update himjlean && claude plugin update himjlean@himjlean` | Redémarrer Claude Code |
| OpenCode | `npx skills update himjlean` | Passer l’en-tête `X-Himjlean-Plugin-Version` à la nouvelle version, puis redémarrer |

## Publier une version

1. Modifier le skill ou les déclarations.
2. Avancer la version dans les six fichiers qui la portent : les deux `plugin.json`, la marketplace Claude, l’en-tête des deux déclarations et l’exemple OpenCode.
3. Ajouter l’entrée dans [CHANGELOG.md](CHANGELOG.md), puis dans le journal du serveur (`src/lib/himjlean/mcp-versions.ts` du site), et y avancer `recommended`.

Version à trois chiffres : correction invisible, ajout, rupture annoncée. Une rupture garde l’ancienne version acceptée 90 jours.

## Tester en local

Les déclarations du serveur local de développement sont dans [examples/dev/](examples/dev/). La marketplace ne les installe pas : on les recopie à la main dans sa propre configuration.
