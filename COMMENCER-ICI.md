# Commencer ici : Git et GitHub en partant de zéro

🇬🇧 *English version: [START-HERE.md](START-HERE.md)*

Salut Daniel 👋 Ce guide t'emmène de « je n'ai jamais utilisé Git » à « je sais partager mes modifications avec Guillaume ».
Compte environ 30 minutes la première fois. Les parties 1 à 3 ne se font qu'une seule fois.

---

## Partie 0 : C'est quoi tout ça ?

- **Git** est un programme sur ton ordinateur qui garde en mémoire toutes les versions des fichiers d'un dossier.
  Chaque version enregistrée s'appelle un **commit** : une photo de l'état des fichiers, avec une petite note qui décrit ce qui a changé.
- **GitHub** est un site web qui garde une copie de ce dossier en ligne, pour que plusieurs personnes puissent le partager.
- Un dossier suivi par Git s'appelle un **dépôt** (en anglais *repository*, ou *repo*).

Tout le fonctionnement tient en trois gestes :

| Geste | Ce que ça veut dire |
|-------|---------------------|
| **pull** (tirer) | Récupérer sur ton ordinateur les dernières modifications présentes sur GitHub |
| **commit** | Enregistrer une photo de tes propres modifications, sur ton ordinateur |
| **push** (pousser) | Envoyer tes commits sur GitHub pour que Guillaume les reçoive |

> 💡 Les commandes et les messages de Git sont en anglais. On garde donc les mots anglais
> (*pull*, *commit*, *push*…), ce sera plus simple pour s'y retrouver.

---

## Partie 1 : Créer un compte GitHub

1. Va sur <https://github.com/signup> et crée un compte gratuit.
2. Choisis un nom d'utilisateur qui te plaît, car il sera visible par les autres.
3. **Envoie ton nom d'utilisateur à Guillaume.** Il va t'inviter sur le projet.
4. Tu vas recevoir une invitation par e-mail (tu peux aussi la trouver sur <https://github.com/notifications>). **Accepte-la.**
   Tant que tu ne l'as pas acceptée, tu peux voir le projet mais pas y envoyer de modifications.

---

## Partie 2 : Installer les outils

Il te faut deux programmes : **Git** et **GitHub CLI** (`gh`), qui s'occupe de la connexion à ton compte.

1. **Installer Git :** <https://git-scm.com/download/win>
   Télécharge et lance l'installateur. Clique sur *Next* à chaque écran, **sauf un** :
   sur l'écran *« Choosing the default editor used by Git »*, choisis **« Use Notepad as Git's default editor »**.
   (Par défaut, c'est un éditeur appelé Vim, très déroutant pour les débutants.)
2. **Installer GitHub CLI :** <https://cli.github.com>
   Télécharge l'installateur Windows et lance-le.
3. **Ouvrir Git Bash.** Cherche « Git Bash » dans le menu Démarrer. Ce sera ton terminal à partir de maintenant.

### Vérifier que tout fonctionne

Tape ces commandes une par une (avec Entrée après chacune) :

```bash
git --version
gh --version
```

Chacune doit afficher un numéro de version. Si tu vois « command not found », ferme Git Bash et rouvre-le.
Si ça ne suffit pas, redémarre l'ordinateur.

> 💡 **Astuces terminal :** on tape une commande puis on appuie sur Entrée. Les majuscules et minuscules comptent.
> Pour coller dans Git Bash, utilise **Maj+Inser** ou clic droit → Paste. (Ctrl+V ne marche pas là-dedans.)

---

## Partie 3 : Configuration (une seule fois)

### Dire à Git qui tu es

Ce nom et cet e-mail seront associés à tes commits. Utilise le même e-mail que ton compte GitHub :

```bash
git config --global user.name "Daniel TonNom"
git config --global user.email "toi@exemple.com"
```

### Se connecter à GitHub

```bash
gh auth login
```

Le programme pose quelques questions. Réponds avec les flèches du clavier et Entrée :

- *Where do you use GitHub?* → **GitHub.com**
- *Preferred protocol?* → **HTTPS**
- *Authenticate Git with your GitHub credentials?* → **Yes**
- *How would you like to authenticate?* → **Login with a web browser**

Un code s'affiche. Appuie sur Entrée, ton navigateur s'ouvre, colle le code et valide. C'est fait.

### Télécharger le projet

```bash
cd ~
git clone https://github.com/guillaumekuc/shared-with-daniel.git
cd shared-with-daniel
```

Ça crée un dossier `shared-with-daniel` dans ton dossier utilisateur (`C:\Users\TonNom\shared-with-daniel`).
Tu peux l'ouvrir dans l'Explorateur de fichiers et modifier les fichiers avec n'importe quel éditeur de texte (le Bloc-notes suffit).

> 💡 `cd` veut dire *change directory* (entrer dans un dossier). `cd ~` t'emmène dans ton dossier utilisateur.
> À chaque fois que tu ouvres Git Bash, tape `cd ~/shared-with-daniel` pour revenir dans le projet.

---

## Partie 4 : Ta première modification 🎉

1. **Récupère la dernière version** (toujours en premier) :
   ```bash
   git pull
   ```
2. **Fais une modification.** Ouvre `guestbook.md` (le livre d'or) dans un éditeur de texte, ajoute une ligne à la fin, par exemple
   `- Daniel : j'ai réussi !`, puis enregistre le fichier.
3. **Regarde ce qui a changé :**
   ```bash
   git status
   ```
   `guestbook.md` apparaît en rouge comme « modified » (modifié).
4. **Prépare la modification** (on dit qu'on l'ajoute à la prochaine photo) :
   ```bash
   git add .
   ```
   Le `.` veut dire « tout ce que j'ai modifié dans ce dossier ». Relance `git status` : c'est maintenant en vert.
5. **Fais le commit** (la photo, avec une petite note) :
   ```bash
   git commit -m "Signature du livre d'or"
   ```
6. **Fais le push** (envoi sur GitHub) :
   ```bash
   git push
   ```

Ouvre maintenant <https://github.com/guillaumekuc/shared-with-daniel> dans ton navigateur : ta modification y est. Guillaume la recevra la prochaine fois qu'il fera `git pull`.

---

## La routine de tous les jours (aide-mémoire)

```bash
cd ~/shared-with-daniel           # aller dans le projet
git pull                          # 1. récupérer les dernières modifs de Guillaume
# ... modifier des fichiers ...
git add .                         # 2. préparer tes modifications
git commit -m "ce que j'ai fait"  # 3. la photo, avec une note
git push                          # 4. partager
```

D'autres commandes pratiques :

```bash
git status          # qu'est-ce qui a changé ? (à utiliser tout le temps, sans risque)
git log --oneline   # liste des commits passés (appuie sur q pour quitter)
```

---

## Bonus : Git avec des boutons plutôt que des commandes (interfaces graphiques)

Quand la routine dans le terminal te paraît claire, tu peux passer à une **interface graphique pour Git** :
une application qui fait les mêmes pull / commit / push avec des boutons, et qui montre tes modifications visuellement.
C'est le même Git en dessous, donc tu peux passer du terminal à l'application quand tu veux.

- **[Sublime Merge](https://www.sublimemerge.com)** : c'est ce qu'utilise Guillaume, donc il pourra t'aider. Rapide et clair.
  Gratuit à l'essai sans limite de durée, il affiche juste de temps en temps un rappel pour acheter une licence.
- **[GitHub Desktop](https://desktop.github.com)** : gratuit, fait par GitHub, très accessible aux débutants.

Pour utiliser l'une ou l'autre, ouvre le dossier `shared-with-daniel` que tu as déjà cloné
(*File → Open Repository* dans Sublime Merge, *File → Add local repository* dans GitHub Desktop).

> 💡 Apprends quand même les commandes d'abord. Elles t'aident à comprendre ce que font les boutons,
> et quand quelque chose coince, les messages d'erreur et l'aide en ligne parlent en commandes.

---

## Quand ça ne marche pas

**`git push` affiche « rejected », « fetch first » ou « non-fast-forward ».**
Guillaume a envoyé quelque chose depuis ton dernier pull. Fais `git pull`, puis `git push` à nouveau.

**Le Bloc-notes s'est ouvert tout seul après `git pull`.**
Git demande une note pour combiner ton travail avec celui de Guillaume. Le texte proposé convient :
ferme simplement le Bloc-notes (enregistre s'il le demande), et Git continue.

**« CONFLICT » après `git pull`.**
Guillaume et toi avez modifié les mêmes lignes. Ouvre le fichier, tu verras quelque chose comme :

```
<<<<<<< HEAD
ta version
=======
la version de Guillaume
>>>>>>> ...
```

Corrige le texte pour qu'il soit comme il faut, supprime les lignes `<<<<<<<`, `=======` et `>>>>>>>`, enregistre, puis :

```bash
git add .
git commit -m "Résolution du conflit"
git push
```

(Les interfaces graphiques comme Sublime Merge rendent les conflits plus faciles à voir et à résoudre.)

**« Permission denied » ou erreur 403 au moment du push.**
Tu n'as pas encore accepté l'invitation de Guillaume (voir la partie 1), ou il faut refaire `gh auth login`.

**« not a git repository ».**
Tu n'es pas dans le bon dossier. Tape `cd ~/shared-with-daniel`.

**Complètement bloqué ?**
Pas de panique, rien ici ne peut être cassé définitivement. Copie ce qu'affiche le terminal et envoie-le à Guillaume.
