# Bandit Level 0 → 1

> ⚠️ Aucun mot de passe n'est publié. Les valeurs sensibles sont masquées : `<FLAG_MASQUE>`

## Énoncé

Se connecter au serveur du jeu en SSH avec l'utilisateur `bandit0`, puis récupérer
le mot de passe du niveau suivant, stocké dans un fichier du répertoire personnel.

## Analyse

Deux choses distinctes ici :

1. **Établir la connexion** — le serveur n'écoute pas sur le port SSH par défaut (22),
   il faut donc le préciser explicitement.
2. **Lire un fichier** — une fois connecté, c'est de la navigation de base : lister,
   identifier, afficher.

## Démarche

1. **Connexion SSH sur le port 2220**

   ```bash
   ssh bandit0@bandit.labs.overthewire.org -p 2220
   ```

   Le mot de passe du niveau 0 est public et fourni par OverTheWire sur la page du jeu.
   À la première connexion, SSH demande de valider l'empreinte du serveur (`known_hosts`).

2. **Lister le contenu du répertoire personnel**

   ```bash
   ls -la
   ```

   `-l` pour voir les permissions et le propriétaire, `-a` pour ne pas rater un
   fichier caché — réflexe à prendre dès le début, plusieurs niveaux suivants en dépendent.

3. **Afficher le fichier repéré**

   ```bash
   cat readme
   ```

   Sortie (masquée) :

   ```text
   The password you are looking for is: <FLAG_MASQUE>
   ```

## Commandes clés

| Commande | Rôle |
|----------|------|
| `ssh user@host -p <port>` | Connexion SSH sur un port non standard |
| `ls -la` | Lister avec détails, fichiers cachés inclus |
| `cat <fichier>` | Afficher le contenu d'un fichier texte |
| `pwd` | Vérifier où l'on se trouve |

## Difficultés rencontrées

Rien de bloquant. Le seul réflexe à ne pas oublier : **le port**. Sans `-p 2220`,
SSH tente le port 22 et la connexion échoue en timeout — une erreur qui ressemble
à un problème réseau alors que c'est juste le mauvais port.

## Ce que j'ai appris

- Un service ne tourne pas forcément sur son port par défaut ; toujours lire la doc
  avant de conclure à une panne.
- `~/.ssh/config` évite de retaper les options à chaque connexion :

  ```sshconfig
  Host bandit*
      HostName bandit.labs.overthewire.org
      Port 2220
      User %h
  ```

  Ensuite `ssh bandit0` suffit.

## Pour aller plus loin

- `man ssh`, `man ssh_config`
- `ssh -v` pour diagnostiquer une connexion qui échoue
