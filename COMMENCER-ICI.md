# Commencer ici : Git et GitHub en partant de zéro

🇬🇧 *English version: [START-HERE.md](START-HERE.md)*

Salut Daniel 👋 Ce guide t'emmène de « je n'ai jamais utilisé Git » à « je sais partager mes modifications avec Guillaume ».

On commence **avec une application à boutons** (Sublime Merge, celle qu'utilise Guillaume).
Une fois à l'aise, on verra **les mêmes gestes en ligne de commande** (niveau 2, à la fin).

Compte environ 30 minutes la première fois. Les parties 1 à 3 ne se font qu'une seule fois.

---

## Partie 0 : C'est quoi tout ça ?

- **Git** est un programme qui garde en mémoire toutes les versions des fichiers d'un dossier.
  Chaque version enregistrée s'appelle un **commit** : une photo de l'état des fichiers, avec une petite note qui décrit ce qui a changé.
- **GitHub** est un site web qui garde une copie de ce dossier en ligne, pour que plusieurs personnes puissent le partager.
- Un dossier suivi par Git s'appelle un **dépôt** (en anglais *repository*, ou *repo*).
- **Sublime Merge** est une application qui te permet d'utiliser Git avec des boutons, sans taper de commandes.

Tout le fonctionnement tient en trois gestes :

| Geste | Ce que ça veut dire |
|-------|---------------------|
| **Pull** (tirer) | Récupérer sur ton ordinateur les dernières modifications présentes sur GitHub |
| **Commit** | Enregistrer une photo de tes propres modifications, sur ton ordinateur |
| **Push** (pousser) | Envoyer tes commits sur GitHub pour que Guillaume les reçoive |

> 💡 Les applications et les messages de Git sont en anglais. On garde donc les mots anglais
> (*Pull*, *Commit*, *Push*…), ce sera plus simple pour s'y retrouver.

---

## Partie 1 : Créer un compte GitHub

1. Va sur <https://github.com/signup> et crée un compte gratuit.
2. Choisis un nom d'utilisateur qui te plaît, car il sera visible par les autres.
3. **Envoie ton nom d'utilisateur à Guillaume.** Il va t'inviter sur le projet.
4. Tu vas recevoir une invitation par e-mail (tu peux aussi la trouver sur <https://github.com/notifications>). **Accepte-la.**
   Tant que tu ne l'as pas acceptée, tu peux voir le projet mais pas y envoyer de modifications.

---

## Partie 2 : Installer les outils

1. **Installer Git :** <https://git-scm.com/download/win>
   Télécharge et lance l'installateur. Clique sur *Next* à chaque écran, **sauf un** :
   sur l'écran *« Choosing the default editor used by Git »*, choisis **« Use Notepad as Git's default editor »**.
   (Par défaut, c'est un éditeur appelé Vim, très déroutant pour les débutants.)
   Git contient aussi le petit outil qui gère la connexion à ton compte GitHub.
2. **Installer Sublime Merge :** <https://www.sublimemerge.com/download>
   Prends la version Windows et lance l'installateur.
   Il est gratuit à l'essai sans limite de durée. Il affiche juste de temps en temps un rappel pour acheter une licence : tu peux le fermer.

---

## Partie 3 : Configuration (une seule fois)

### Dire à Git qui tu es

Ton nom et ton e-mail seront associés à chacun de tes commits. Ce sont les deux seules commandes
du guide avant le niveau 2 : tu n'as qu'à les copier-coller.

1. Dans le menu Démarrer, cherche et ouvre **Git Bash** (une fenêtre noire s'ouvre).
2. Copie la première ligne ci-dessous, colle-la avec **Maj+Inser** (ou clic droit → Paste), remplace par ton nom, puis appuie sur Entrée.
3. Pareil pour la deuxième ligne, avec **le même e-mail que ton compte GitHub**.

```bash
git config --global user.name "Daniel TonNom"
git config --global user.email "toi@exemple.com"
```

Tu peux fermer Git Bash.

### Télécharger le projet (on dit « cloner »)

1. Ouvre **Sublime Merge**. Tu arrives sur la page d'accueil :

   ![Page d'accueil de Sublime Merge](https://www.sublimemerge.com/images/clone_page.png)

2. Clique sur **Clone Repository** (ou passe par le menu *File → Clone Repository…*).
3. Remplis les champs :
   - **Source URL :** `https://github.com/guillaumekuc/shared-with-daniel.git`
   - **Destination Path :** l'endroit où mettre le dossier, par exemple `C:\Users\TonNom\shared-with-daniel`
4. Clique sur **Clone**. Le projet s'ouvre dans Sublime Merge.

Le dossier `shared-with-daniel` existe maintenant sur ton ordinateur. Tu peux l'ouvrir dans l'Explorateur de fichiers
et modifier les fichiers avec n'importe quel éditeur de texte (le Bloc-notes suffit).

### Faire le tour de l'écran

![Vue d'ensemble de Sublime Merge](https://www.sublimemerge.com/images/overview.png)

- **Au centre :** l'historique, c'est-à-dire la liste des commits, du plus récent au plus ancien.
  Tout en haut, la ligne **Working Directory** représente tes modifications pas encore enregistrées.
- **En haut à droite :** les boutons **Pull** et **Push**.

![Boutons Pull et Push](https://www.sublimemerge.com/images/push_and_pull.png)

---

## Partie 4 : Ta première modification 🎉

1. **Récupère la dernière version :** clique sur **Pull** (en haut à droite). À faire *toujours* en premier.
2. **Fais une modification.** Dans l'Explorateur de fichiers, ouvre `guestbook.md` (le livre d'or) avec le Bloc-notes.
   Ajoute une ligne à la fin, par exemple `- Daniel : j'ai réussi !`, puis enregistre.
3. **Reviens dans Sublime Merge.** Clique sur la ligne **Working Directory** en haut de l'historique.
   `guestbook.md` apparaît dans la liste **Unstaged Files** (fichiers modifiés, pas encore préparés).
   Les lignes ajoutées sont en vert, les lignes supprimées en rouge.
4. **Prépare la modification (« Stage ») :** clique sur le bouton **Stage** à côté du fichier
   (ou **Stage All** pour tout préparer d'un coup). Le fichier passe dans **Staged Files**.

   ![Fichiers à préparer](https://www.sublimemerge.com/images/file_tabs.png)

5. **Fais le commit :** tout en haut, écris une petite note dans le champ du message,
   par exemple `Signature du livre d'or`, puis clique sur **Commit**.

   ![Champ du message de commit](https://www.sublimemerge.com/images/commit_message.png)

   Ton commit apparaît maintenant en haut de l'historique. Il n'est encore que **sur ton ordinateur**.

6. **Envoie-le (« Push ») :** clique sur **Push**.
   **La toute première fois**, une fenêtre GitHub s'ouvre pour te connecter : choisis
   **Sign in with your browser**, connecte-toi dans le navigateur et valide. Les fois suivantes, ce ne sera plus demandé.

Ouvre maintenant <https://github.com/guillaumekuc/shared-with-daniel> dans ton navigateur : ta modification y est.
Guillaume la recevra la prochaine fois qu'il cliquera sur Pull.

---

## La routine de tous les jours

1. **Pull** pour récupérer les nouveautés de Guillaume
2. Modifier des fichiers (dans ton éditeur habituel)
3. Dans Sublime Merge : **Stage** les fichiers
4. Écrire un message, puis **Commit**
5. **Push**

C'est tout. Ces 5 étapes te suffisent pour 95 % des cas.

---

## Quand ça ne marche pas

**Le Push est refusé (« rejected », « fetch first », « non-fast-forward »).**
Guillaume a envoyé quelque chose depuis ton dernier Pull. Clique sur **Pull**, puis de nouveau sur **Push**.

**« Conflict » après un Pull.**
Guillaume et toi avez modifié les mêmes lignes, et Git ne sait pas quelle version garder.
Dans Sublime Merge, le fichier apparaît dans une section **Merge Conflicts**. Ouvre-le dans l'outil de fusion :

![Outil de résolution de conflits](https://www.sublimemerge.com/images/merge_tool.png)

Ta version et celle de Guillaume sont côte à côte, et le résultat est au milieu.
Choisis pour chaque morceau quelle version garder, enregistre, puis fais **Stage**, **Commit** et **Push** comme d'habitude.
Si tu as un doute, demande à Guillaume : c'est plus simple à deux la première fois.

**Le Push demande un mot de passe, ou affiche « Permission denied » / erreur 403.**
- Vérifie que tu as bien accepté l'invitation de Guillaume (voir la partie 1).
- Vérifie que Git est bien installé (partie 2) : c'est lui qui affiche la fenêtre de connexion GitHub.
- Si ça bloque toujours : dans Sublime Merge, *Preferences → Advanced* (ou *Tools → Preferences*),
  cherche le réglage **Git Binary** et choisis **System**, puis réessaie.

**Complètement bloqué ?**
Pas de panique, rien ici ne peut être cassé définitivement. Fais une capture d'écran et envoie-la à Guillaume.

---

## Niveau 2 : la même chose en ligne de commande

Quand la routine avec les boutons te paraît naturelle, tu peux apprendre les commandes.
Ça vaut le coup : les messages d'erreur et l'aide en ligne parlent presque toujours en commandes,
et tu comprendras mieux ce que font les boutons. C'est le même Git en dessous :
tu peux passer de Sublime Merge au terminal quand tu veux, sur le même dossier.

### Ouvrir un terminal dans le projet

Dans l'Explorateur de fichiers, fais un clic droit dans le dossier `shared-with-daniel` →
**Open Git Bash here** (sous Windows 11, il faut parfois cliquer d'abord sur *Afficher d'autres options*).

> 💡 **Astuces terminal :** on tape une commande puis on appuie sur Entrée. Les majuscules et minuscules comptent.
> Pour coller dans Git Bash, utilise **Maj+Inser** ou clic droit → Paste. (Ctrl+V ne marche pas là-dedans.)

### Correspondance boutons → commandes

| Dans Sublime Merge | En ligne de commande |
|--------------------|----------------------|
| Bouton **Pull** | `git pull` |
| Regarder la ligne *Working Directory* | `git status` |
| Bouton **Stage All** | `git add .` |
| Écrire le message puis **Commit** | `git commit -m "ton message"` |
| Bouton **Push** | `git push` |
| Regarder l'historique | `git log --oneline` (appuie sur `q` pour quitter) |
| *File → Clone Repository* | `git clone https://github.com/guillaumekuc/shared-with-daniel.git` |

### La routine en commandes

```bash
git pull                          # 1. récupérer les dernières modifs de Guillaume
# ... modifier des fichiers ...
git status                        #    (voir ce qui a changé : rouge = pas encore préparé)
git add .                         # 2. préparer tout ce qui a changé (le « . » veut dire « tout »)
git status                        #    (maintenant c'est vert)
git commit -m "ce que j'ai fait"  # 3. la photo, avec une note
git push                          # 4. partager
```

**Exercice :** signe une deuxième fois le livre d'or, mais cette fois uniquement avec ces commandes.
Ensuite, regarde dans Sublime Merge : ton commit y apparaît aussi.

### Pièges spécifiques au terminal

**« not a git repository ».** Tu n'es pas dans le bon dossier. Tape `cd ~/shared-with-daniel`
(ou rouvre Git Bash avec le clic droit dans le dossier).

**Le Bloc-notes s'ouvre tout seul après `git pull`.** Git demande une note pour combiner ton travail
avec celui de Guillaume. Le texte proposé convient : ferme le Bloc-notes (enregistre s'il le demande), et Git continue.

**Conflit dans le terminal.** Le fichier contient des marqueurs comme ceci :

```
<<<<<<< HEAD
ta version
=======
la version de Guillaume
>>>>>>> ...
```

Corrige le texte, supprime les lignes `<<<<<<<`, `=======` et `>>>>>>>`, enregistre, puis
`git add .`, `git commit -m "Résolution du conflit"` et `git push`.
(Ou ouvre Sublime Merge, qui est souvent plus confortable pour ça.)

---

*Images : documentation officielle de [Sublime Merge](https://www.sublimemerge.com/docs/getting_started).
L'interface peut avoir un peu changé depuis, mais les boutons portent les mêmes noms.*
