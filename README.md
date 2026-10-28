# CCNA Lab — entraînement CCNA 3 ENSA v7

Site statique, responsive, sans serveur et gratuit, prêt pour **GitHub Pages**.

## Ouvrir le site

Ouvre `index.html` dans un navigateur. Aucune installation n'est nécessaire. Les illustrations des questions sont chargées depuis les URLs du site source : il faut une connexion pour les afficher. Les QCM fonctionnent sans réseau.

## Publier sur GitHub Pages

1. Décompresse le ZIP téléchargé.
2. Sur GitHub, crée un dépôt public, par exemple `ccna3-ensa-quiz`.
3. Transfère **le contenu du dossier** à la racine du dépôt (`index.html`, `style.css`, `app.js`, les dossiers `data/` et `assets/`, ainsi que `README.md`). Ne transfère pas seulement le ZIP.
4. Dans **Settings > Pages > Build and deployment**, sélectionne **Deploy from a branch**, branche `main` et dossier `/(root)`, puis clique sur **Save**.
5. Quand GitHub a terminé la publication, ton site aura une URL du type `https://TON-PSEUDO.github.io/ccna3-ensa-quiz/`.

## Fonctionnalités

- Tirages aléatoires de 20, 40, 70, 100 ou toutes les questions disponibles.
- Modes « Examen blanc », « Révision guidée » et « Mes erreurs », avec **correction instantanée dans tous les modes**.
- Choix multiples et simples ; ordre des questions **et des réponses** mélangé.
- **Clique sur une ou plusieurs réponses, puis sur « Valider ma réponse »** : bonne réponse encadrée en **vert** ; mauvaise réponse en **rouge**, et bonne(s) réponse(s) affichée(s) en **vert** immédiatement.
- Navigation par numéro de question, signalement des questions à revoir. Les questions non validées ne rapportent pas de points.
- Minuteur paramétrable (facultatif), correction détaillée, scores par thème.
- Historique des 30 dernières tentatives ; reprise d'un examen après actualisation.
- Filtre par thème et import de questions personnelles en JSON.
- Entièrement autonome en HTML/CSS/JS : pas de serveur, compte ou service payant.

## Contenu du fichier fourni

Le HTML transmis a permis d'extraire **213 entrées** : **205 QCM corrigibles automatiquement** et **8 cas particuliers** (associations, absence de réponses identifiées, ou incohérence). Parmi ces 8 cas, une question demande deux bonnes réponses mais une seule est étiquetée comme correcte dans le HTML. Elle a été exclue du calcul de score.

Les QCM et corrigés sont **issus du HTML fourni**, dont les éléments renvoient au site `ccnareponses.com`. Ils ne sont pas validés par Cisco, ne constituent pas une banque officiellement certifiée et peuvent contenir des erreurs. Les illustrations ne sont pas redistribuées : elles restent chargées depuis les liens URL contenus dans le fichier.

## Structure

```text
ccna3-ensa-quiz/
├── index.html
├── style.css
├── app.js
├── README.md
├── assets/
│   └── favicon.svg
└── data/
    ├── questions-source.js       # données accessibles au navigateur, sans fetch
    ├── questions-source.json     # même banque, format modifiable
    └── format-exemple.json       # exemple d'import
```

## Modifier la banque

- Les questions incluses se trouvent dans `data/questions-source.json`.
- Le site charge `data/questions-source.js`. Si tu modifies la version JSON, recopie son contenu dans `questions-source.js` en conservant l'instruction JavaScript `window.CCNA_SOURCE = ...;`.
- Pour ajouter des questions sans modifier le code, ouvre l'onglet **Banque de questions**, choisis un fichier JSON au format de `data/format-exemple.json`. Cela les ajoute **uniquement à ce navigateur**. Pour les publier pour tous, ajoute-les dans le dépôt.
- Les bonnes réponses sont référencées par leurs indices **à partir de 0**. Pour deux bonnes réponses, par exemple `"correct": [0, 2]`.

## Confidentialité

Les résultats, examens en cours et imports personnels sont stockés en `localStorage`, sur ton navigateur. Il n'y a pas de serveur applicatif. Vider les données du navigateur peut supprimer ton historique.
