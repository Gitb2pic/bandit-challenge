# 🐧 OverTheWire — Bandit : carnet de résolution

> Documentation personnelle de ma progression sur le wargame
> [**Bandit**](https://overthewire.org/wargames/bandit) d'OverTheWire.
> L'objectif : consolider ma maîtrise de la ligne de commande Linux, des accès SSH
> et des bases de la sécurité système, dans une optique **DevOps / SysAdmin**.

![Linux](https://img.shields.io/badge/Linux-shell-black?logo=linux&logoColor=white)
![SSH](https://img.shields.io/badge/SSH-OpenSSH-blue)
![Niveaux](https://img.shields.io/badge/niveaux-0%20%E2%86%92%2034-green)
![Flags](https://img.shields.io/badge/flags-non%20publi%C3%A9s-red)

---

## ⚠️ Politique « pas de flags »

Ce dépôt **ne contient aucun mot de passe** (flag) des niveaux de Bandit.

Publier les flags priverait les autres apprenants de l'exercice et va à l'encontre
de l'esprit du wargame. Ce que vous trouverez ici, c'est le **raisonnement** :
l'analyse de l'énoncé, les commandes et les options utilisées, les pièges rencontrés,
et ce que chaque niveau m'a appris.

Dans les extraits de terminal, les valeurs sensibles sont remplacées par :

```text
<FLAG_MASQUE>
```

---

## 🎯 Pourquoi ce dépôt

- **Montrer une démarche**, pas seulement un résultat : comment j'attaque un problème inconnu,
  quelles hypothèses je teste, comment je vérifie.
- **Capitaliser** : un mémo réutilisable sur `find`, `grep`, les permissions, `ssh`, `nc`,
  `openssl`, `git`, la compression, les tâches `cron`…
- **Alimenter mon portfolio** : une preuve concrète d'autonomie sur un environnement Linux,
  compétence de base du métier DevOps.

---

## 🗂️ Structure du dépôt

```text
bandit-challenge/
├── README.md              # ce fichier
├── .gitignore             # garde-fou : bloque clés et fichiers de flags
├── levels/
│   ├── _template.md       # canevas commun à tous les writeups
│   ├── level-00.md
│   ├── level-01.md
│   └── ...
├── notes/
│   ├── cheatsheet.md      # commandes retenues, par thème
│   └── ssh.md             # connexion, options, clés
└── assets/                # captures d'écran (flags masqués)
```

---

## 🧩 Format d'un writeup

Chaque fichier `levels/level-XX.md` suit le même canevas :

```markdown
# Bandit Level XX → XX+1

## Énoncé
Reformulation courte de l'objectif du niveau.

## Analyse
Ce que l'énoncé implique, les hypothèses de départ.

## Démarche
1. Étape, avec la commande et **pourquoi** cette commande.
2. ...

## Commandes clés
| Commande | Rôle |
|----------|------|
| `...`    | ...  |

## Difficultés rencontrées
Ce qui a coincé, et comment je m'en suis sorti.

## Ce que j'ai appris
Le concept à retenir (au-delà du niveau lui-même).
```

---

## 🔌 Se connecter à Bandit

Le jeu est accessible en SSH sur le port **2220** :

```bash
ssh bandit0@bandit.labs.overthewire.org -p 2220
```

Le mot de passe du niveau 0 est public et fourni par OverTheWire.
Les suivants se gagnent niveau après niveau — et ne sont pas ici. 🙂

Astuce confort — un bloc dans `~/.ssh/config` :

```sshconfig
Host bandit*
    HostName bandit.labs.overthewire.org
    Port 2220
    User %h
```

---

## 📈 Progression

| Niveaux | Thématique principale | État |
|---------|----------------------|------|
| 00 → 04 | Connexion SSH, lecture de fichiers, noms de fichiers exotiques | 🔄 |
| 05 → 09 | `find` et ses filtres, `grep`, données binaires, `strings` | ⏳ |
| 10 → 14 | Encodages (base64, ROT13), archives imbriquées, clés SSH | ⏳ |
| 15 → 19 | Réseau : `nc`, `openssl s_client`, binaires `setuid` | ⏳ |
| 20 → 24 | Démons, `cron`, scripts appelés par d'autres utilisateurs | ⏳ |
| 25 → 29 | Shells restreints, éditeurs, `git` comme vecteur | ⏳ |
| 30 → 34 | `git` avancé (branches, tags, hooks) | ⏳ |

Légende : ✅ terminé · 🔄 en cours · ⏳ à venir

---

## 🛠️ Compétences travaillées

- **Shell Linux** : navigation, redirections, pipes, quoting, gestion des caractères spéciaux
- **Recherche** : `find` (`-size`, `-user`, `-group`, `-perm`, `-newer`), `grep`, `sort`, `uniq`, `xxd`
- **Permissions & utilisateurs** : bits `setuid`, appartenance aux groupes, principe du moindre privilège
- **Réseau** : `nc`, `telnet`, TLS avec `openssl s_client`, notion de port et de service
- **Formats & encodages** : base64, ROT13, `gzip`/`bzip2`/`tar`, détection avec `file`
- **Automatisation** : lecture de `crontab`, scripts shell, sécurité des scripts privilégiés
- **Git** : exploration d'un historique, branches, tags, objets

---

## 📚 Ressources

- [OverTheWire — Bandit](https://overthewire.org/wargames/bandit)
- `man <commande>` et `<commande> --help` — la première réponse à chercher
- [explainshell.com](https://explainshell.com) pour décortiquer une commande complexe

---

## 👤 Auteur

Dépôt maintenu dans le cadre de mon apprentissage **DevOps**.
Les writeups sont rédigés après résolution personnelle de chaque niveau.
