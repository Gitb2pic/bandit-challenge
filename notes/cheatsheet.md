# 📝 Cheatsheet — commandes retenues

Mémo personnel alimenté au fil des niveaux. Classé par thème, pas par niveau.

## Navigation & lecture

| Commande | Usage |
|----------|-------|
| `ls -la` | Lister avec permissions et fichiers cachés |
| `cat`, `less`, `head`, `tail` | Afficher un fichier |
| `file <fichier>` | Identifier le type réel (le nom ment souvent) |
| `stat <fichier>` | Taille, dates, inode, permissions |

### Noms de fichiers pièges

| Cas | Solution |
|-----|----------|
| Espaces dans le nom | `cat "mon fichier"` ou `cat mon\ fichier` |
| Nom commençant par `-` | `cat ./-fichier` ou `cat < -fichier` |
| Caractères invisibles | `ls -b` pour les révéler |

## Recherche

```bash
find / -type f -size 1033c -user bandit7 -group bandit6 2>/dev/null
```

| Option | Rôle |
|--------|------|
| `-type f` / `-type d` | Fichier / répertoire |
| `-size 1033c` | Taille exacte en octets (`c`), `k`, `M` possibles |
| `-user` / `-group` | Propriétaire / groupe |
| `-perm` | Permissions (`-perm -u=s` pour les binaires setuid) |
| `-newer <ref>` | Modifié après un fichier de référence |
| `2>/dev/null` | Masquer les « Permission denied » qui noient la sortie |

```bash
grep -r "motif" .        # récursif
grep -i / -v / -n        # insensible à la casse / inverse / numéro de ligne
sort | uniq -u           # garder les lignes uniques (attention : sort obligatoire avant)
strings <binaire>        # extraire le texte lisible d'un fichier binaire
xxd <fichier> | head     # dump hexadécimal
```

## Encodages & compression

```bash
base64 -d <fichier>              # décoder du base64
tr 'A-Za-z' 'N-ZA-Mn-za-m'       # ROT13
gzip -d / bzip2 -d / tar xf      # décompresser
```

Réflexe : `file` **avant** de décompresser — l'extension est souvent absente ou fausse.

## Réseau

```bash
nc <host> <port>                 # connexion TCP brute
nc -lvnp <port>                  # se mettre en écoute
openssl s_client -connect host:port   # même chose mais en TLS
```

## Permissions

| Notion | À retenir |
|--------|-----------|
| `setuid` | Le binaire s'exécute avec les droits de son **propriétaire** |
| `chmod 600` | Obligatoire pour une clé privée SSH, sinon SSH la refuse |
| `sudo -l` | Lister ce que l'on a le droit d'exécuter |

## Git

```bash
git log --oneline --all     # tout l'historique, toutes les branches
git show <commit>           # contenu d'un commit
git branch -a / git tag     # branches et tags
git diff <a> <b>            # comparer deux références
```
