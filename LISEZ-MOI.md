# Xiǎo Bāng · test d'écoute hors ligne

But : vérifier sur mon OPPO que le téléphone peut **écouter du chinois et le transcrire tout seul, sans internet**, et mesurer la vitesse et la précision avant de construire l'appli native.

Le modèle d'écoute est **Whisper** (OpenAI, licence MIT, usage commercial autorisé). Le moteur qui le fait tourner dans le navigateur est **transformers.js** (Hugging Face, licence Apache 2.0).

## Contenu du dossier

| Fichier | Rôle |
|---|---|
| `index.html` | la page de test (70 phrases issues du prototype) |
| `sw.js` | garde la page, le moteur et le modèle sur le téléphone pour le mode avion |
| `LISEZ-MOI.md` | ce mode d'emploi |

## 1. Mettre la page en ligne (une fois, avec GitHub Desktop)

La page doit être servie en **https** pour avoir accès au micro. GitHub Pages le fait gratuitement.

1. GitHub Desktop → **File → Add Local Repository…** → choisir le dossier `~/Mandarin/xiao-bang/test-ecoute` → cliquer **create a repository** → **Create Repository**.
2. Faire le commit :
   - **Summary** : `Ajout de la page de test d'écoute hors ligne`
   - **Description** : `Page web qui fait tourner Whisper sur le téléphone, sans internet après le premier chargement, pour mesurer vitesse et précision sur les phrases de Xiao Bang avant de construire l'appli native.`
3. **Publish repository** → nom `test-ecoute` → **décocher « Keep this code private »** (GitHub Pages gratuit demande un dépôt public ; ce dossier ne contient que la page de test et les phrases, rien de sensible).
4. Sur github.com, ouvrir le dépôt → **Settings → Pages** → *Source* : **Deploy from a branch** → *Branch* : **main** / **(root)** → **Save**.
5. Attendre 1 à 2 minutes : l'adresse s'affiche, du type `https://TON-COMPTE.github.io/test-ecoute/`.

> Ne mets pas le dossier `xiao-bang` entier en public : la fiche concept doit rester privée.

## 2. Préparer sur le téléphone (une fois, en Wi-Fi)

1. Sur l'OPPO, ouvrir l'adresse dans **Chrome**.
2. Choisir **Base** puis **Préparer** : environ 80 Mo à télécharger. Attendre « Prêt ».
3. Optionnel : menu **⋮ → Ajouter à l'écran d'accueil**.
4. Autoriser le **micro** quand Chrome le demande.

## 3. Tester en mode avion

1. Activer le **mode avion**, puis recharger la page : elle doit s'ouvrir quand même (pastille verte « Mode hors ligne »).
2. Rappuyer sur **Préparer** : le modèle se recharge depuis le téléphone, sans téléchargement.
3. Choisir une phrase, appuyer sur le gros bouton, faire dire la phrase, rappuyer pour arrêter.
4. Lire le résultat : ce qui a été entendu, le **temps de calcul**, le **% de caractères justes**, les **mots clés** trouvés (二楼, 右转…).

### Plan de test conseillé (environ 20 minutes)

| Essai | Modèle | Qui parle | Où |
|---|---|---|---|
| 1 | Base | moi | au calme |
| 2 | Base | une personne qui parle chinois (ou une vidéo) | au calme |
| 3 | Base | la même | avec du bruit (télé, rue) |
| 4 | Tiny | la même | au calme |
| 5 | Small | la même | au calme |

Faire 5 phrases par essai, de préférence des scènes Aéroport et Fournisseur.

## 4. Renvoyer les résultats

Bouton **Copier les résultats** → coller dans la conversation avec Claude. On choisira le modèle à embarquer dans l'appli (vitesse ou précision) et on saura s'il faut un modèle spécialisé mandarin.

## Ce que ce test ne mesure pas encore

- La **traduction** (chinois → français) : prochaine étape, avec un modèle sous licence permissive.
- La **vitesse en appli native** : une vraie appli Android sera **plus rapide** que le navigateur. Si le test est acceptable ici, il sera meilleur dans l'appli.
