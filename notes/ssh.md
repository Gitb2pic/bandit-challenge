# 🔐 Notes SSH

## Connexion à Bandit

```bash
ssh bandit<N>@bandit.labs.overthewire.org -p 2220
```

Le port **2220** est imposé par OverTheWire. Sans `-p`, SSH tente le port 22 et
la connexion part en timeout.

## Simplifier avec `~/.ssh/config`

```sshconfig
Host bandit*
    HostName bandit.labs.overthewire.org
    Port 2220
    User %h
```

`%h` reprend le nom saisi comme utilisateur : `ssh bandit12` se connecte en `bandit12`.

## Utiliser une clé privée trouvée dans un niveau

```bash
chmod 600 /chemin/vers/cle
ssh -i /chemin/vers/cle bandit<N>@bandit.labs.overthewire.org -p 2220
```

SSH **refuse** une clé privée dont les permissions sont trop larges
(`UNPROTECTED PRIVATE KEY FILE!`). Le `chmod 600` n'est pas optionnel.

Si le répertoire courant n'est pas inscriptible, copier la clé dans `/tmp/<dossier>`
créé pour l'occasion (`mktemp -d`).

## Diagnostiquer

| Commande | Usage |
|----------|-------|
| `ssh -v` (ou `-vvv`) | Trace détaillée de la négociation |
| `ssh-keygen -R <host>` | Purger une empreinte obsolète de `known_hosts` |

## Divers

- `ssh user@host -p 2220 <commande>` exécute une commande sans ouvrir de session interactive.
- Un shell restreint peut refuser certaines commandes : tester `ssh ... -t "bash --noprofile"`.
