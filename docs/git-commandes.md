# Commandes Git

Git enregistre l’historique de tes fichiers sur ton poste et l’échange avec GitHub. Le fork et la demande de fusion (Pull Request) se font sur le site GitHub : voir [Fork et demande de fusion sur GitHub](github-demande-de-fusion.md).

## Vérifier sa configuration

Dans un terminal :

```sh
git --version
git config --global user.name
git config --global user.email
```

Si le nom ou le courriel ne s’affiche pas, les renseigner, avec le courriel du compte GitHub :

```sh
git config --global user.name "Prénom Nom"
git config --global user.email "ton-courriel@exemple.fr"
```

## Cloner son fork

Sur la page du fork, cliquer sur **Code** et copier l’adresse HTTPS. Dans un terminal, se placer dans le dossier des projets :

```sh
git clone https://github.com/<ton-compte>/assistant-fiches-support.git
cd assistant-fiches-support
git status
```

`git status` indique la branche courante, `main`, et les fichiers modifiés. À utiliser avant chaque commit.

## Commiter et pousser

Après l’enregistrement de `docs/besoin.md` :

```sh
git status
git add docs/besoin.md
git commit -m "Rédige le besoin de l’assistant"
git push
```

- `git add` choisit les fichiers à inclure dans le prochain commit.
- `git commit` enregistre ces fichiers dans l’historique local, avec un message qui décrit le changement.
- `git push` publie tes commits dans ton fork. Au premier `git push`, GitHub demande de se connecter.

Pour vérifier, ouvrir le fork sur GitHub : `docs/besoin.md` contient le travail poussé.

## Comparer deux versions

```sh
git log --oneline
git diff <commit-avant> <commit-après> -- docs/besoin.md
```

`git log --oneline` affiche l’identifiant court de chaque commit, du plus récent au plus ancien. `git diff` montre les lignes retirées (`-`) et ajoutées (`+`) entre les deux commits. La touche `q` quitte l’affichage.
