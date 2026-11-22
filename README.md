# himjlean

Connectez votre agent de code à vos projets himjlean pour retrouver vos tâches, les organiser et avancer sur votre cadrage stratégique sans quitter votre conversation.

Le plugin installe le serveur MCP himjlean et les consignes qui permettent à l’agent de l’utiliser correctement. Il est disponible pour **Codex** et **Claude Code**. L’intégration **OpenCode** est proposée en bêta.

La version 0.3.0 ajoute les consignes pour les organisations partagées, les rôles Propriétaire, Admin et Reader, les invitations et les notifications. Le [guide complet](https://www.himjconception.com/himjlean#documentation) présente les outils et les droits de chaque rôle.

## Avant de commencer

- disposer d’un [compte himjlean](https://www.himjconception.com/himjlean) ;
- avoir installé Codex, Claude Code ou OpenCode ;
- autoriser l’accès au compte himjlean dans le navigateur pendant l’installation.

## Installer le plugin

### Codex

```sh
codex plugin marketplace add himj69/himjlean-plugin
codex plugin add himjlean@himjlean
codex mcp login himjlean
```

Une page himjlean s’ouvre dans le navigateur. Vérifiez le compte affiché, puis autorisez Codex.

### Claude Code

```sh
claude plugin marketplace add himj69/himjlean-plugin
claude plugin install himjlean@himjlean
```

Dans Claude Code, ouvrez `/mcp`, sélectionnez **himjlean**, puis **Authenticate**. Vérifiez ensuite le compte affiché dans le navigateur et autorisez l’accès.

### OpenCode — bêta

1. Fusionnez la configuration de [`opencode/opencode.json`](opencode/opencode.json) avec votre propre fichier `opencode.json`.
2. Installez le skill et lancez l’autorisation :

```sh
npx skills add himj69/himjlean-plugin --skill himjlean
opencode mcp auth himjlean
```

Conservez les autres serveurs déjà présents dans votre configuration OpenCode.

## Vérifier la connexion

Après l’installation, ouvrez une nouvelle conversation et demandez :

> Liste les projets de mon organisation avec himjlean.

L’agent doit utiliser les outils du serveur `himjlean`. S’ils n’apparaissent pas immédiatement, redémarrez votre client puis ouvrez une nouvelle conversation.

## Mettre à jour

Le serveur vous prévient lorsqu’une nouvelle version du plugin est disponible.

| Client | Commande de mise à jour | Ensuite |
| --- | --- | --- |
| Codex | `codex plugin marketplace upgrade himjlean && codex plugin add himjlean@himjlean` | Ouvrir une nouvelle conversation |
| Claude Code | `claude plugin marketplace update himjlean && claude plugin update himjlean@himjlean` | Redémarrer Claude Code |
| OpenCode | `npx skills update himjlean` | Mettre à jour la version indiquée dans `opencode.json`, puis redémarrer |

## Liens utiles

- [Découvrir himjlean](https://www.himjconception.com/himjlean)
- [Documentation et installation](https://www.himjconception.com/himjlean#documentation)
- [Consulter les changements](CHANGELOG.md)
- [Licence MIT](LICENSE)
