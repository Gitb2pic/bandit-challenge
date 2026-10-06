# Bandit Level 1 → 2

> ⚠️ Aucun mot de passe n'est publié. Les valeurs sensibles sont masquées : `<FLAG_MASQUE>`

## Énoncé

Le mot de passe est dans le fichier -. Il est ce trouve dans le repertoire personnel.

## Analyse

**Afficher le flag avec commande cat** le fichier lorsqu'on utilise `cat -`,  il ne passe rien, il attend une entre du claviez.

## Démarche

1. **Pour affichier le fichier -  il faut utilise les chemin relatif.** 

   ```bash
   ls 
   -
   cat ./
   flag level 2
   ```

## Commandes clés

| Commande | Rôle |
|----------|------|
| `cat < fichier >`    | Affiche le contenue du fichier|
|  `.`| Indique le repertoire où tu te trouve actuellement| 
|`/`| sépare le nom du dossier du nom du fichier|

## Difficultés rencontrées

Comprendre pourquoi, utilisation classique de cat ne fonctionne pas.

## Ce que j'ai appris

Certain commande du système linux comme `cat`, `grep` et `tar` etc...
devant - agit comment un raccourci pour les libreris standard `STDIN` et `STDOUT`.

## Pour aller plus loin

- [How to open a "-" dashed filename using terminal?](https://stackoverflow.com/questions/42187323/how-to-open-a-dashed-filename-using-terminal)
