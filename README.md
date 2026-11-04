# Portfolio — AMOUSSOU-GUENOU Donald

Portfolio personnel dans **un seul fichier statique**, bilingue français/anglais. Aucune dépendance, aucun build, aucune image externe : `index.html` contient l'écran d'entrée et le portfolio.

Adresse une fois publié : **https://lonerfy.github.io/portfolio/**

## L'écran d'entrée

Écran noir, une phrase seule — « Approchez. » — puis le rideau se lève : le portrait occupe toute la hauteur à droite et déborde du cadre, le menu tient la gauche en grandes lames obliques, les compteurs en bas. Choisir une entrée fait basculer vers la section correspondante du portfolio ; le bouton *accueil*, en haut à droite du portfolio, ramène à l'écran d'entrée. Une adresse directe comme `#projets` saute l'entrée et ouvre la section.

Le portrait est un nuage de particules sur canvas qui compose successivement quatre photos. Entre deux photos les points se dispersent puis se rassemblent. Ils fuient le curseur, un clic sur le cadre passe à la photo suivante, et le cycle tourne seul toutes les sept secondes. Survoler une entrée du menu change la légende sous le portrait.

Les nuages sont **précalculés et intégrés au fichier** : chaque point tient en quatre caractères en base 36 qui encodent sa position dans une grille de 300 × 380 et son niveau de clarté de 0 à 3. Aucune image n'est chargée au moment de l'affichage, donc rien à héberger et rien qui puisse échouer. Les données sont dans le tableau `PORTRAITS`, en tête du script.

## Le portfolio

- Cinq sections : accueil, profil, projets, parcours, contact
- Dix-sept projets, fiche détaillée, badge « démo en ligne » et badge « dépôt public »
- Douze démos reliées : Duo's Terminal, LyricStage, Neon Arcade, Nekhen Duels, Archer Quest, ORBITAL, Morphogène, Snake, Parade, Cobaye, GIF Forge, Portfolio & CV Generator
- Bascule **FR / EN** sur tout le contenu, langue devinée du navigateur au premier chargement
- Adresses directes : `#projets` ouvre la section, `#projets/snake` ouvre la fiche
- Navigation clavier : `↑` `↓` changent de section, `1` à `5` en accès direct, `Échap` ferme
- Trois ambiances au même bouton, chacune avec son identité :
  - **clair** — blanc pur, noir pur, aucune teinte : l'ambiance d'ouverture
  - **cuivre** — noir, argent, cuivre oxydé, accent vert phosphore
  - **acier** — noir bleuté, métal froid, accent glacier
- Le site s'ouvre en **mode clair**, animations actives. Le bouton **animations / sobre** permet de tout couper ; le bouton d'ambiance fait défiler clair, cuivre, acier
- Mise en page d'impression propre : `Ctrl+P` donne un document noir sur blanc, toutes sections dépliées
- Métadonnées de partage, favicon vectorielle intégrée

## Modifier le contenu

Tout est en haut du `<script>`. Chaque texte est un objet `{fr, en}`.

| Tableau | Ce qu'il alimente |
|---|---|
| `PORTRAITS` | les nuages de points du portrait |
| `I` | libellés d'interface, titres, accroche, menu d'entrée et ses légendes |
| `PROJETS` | la grille et les fiches |
| `COMPETENCES` | les six cartes du profil |
| `PARCOURS` | la chronologie |
| `LIENS` | la section contact |

Un projet se déclare ainsi :

```js
{nom:"Snake", tag:{fr:"jeu",en:"game"},
 public:true, lien:GITHUB+"/Snake",
 demo:"https://lonerfy.github.io/Snake/",
 resume:{fr:"Une phrase sur la carte.", en:"One line on the card."},
 texte:{fr:"Le paragraphe de la fiche.", en:"The detail paragraph."},
 pile:["TypeScript"]}
```

`public:true` affiche le badge « dépôt public » et le bouton *Voir le code*. `demo` ajoute le badge « démo en ligne » et le bouton *Ouvrir la démo*. Les deux sont facultatifs.

## À compléter

- **Neon Arcade**, **ORBITAL** et **Portfolio & CV Generator** : fiches encore vides, alors que les trois ont une démo en ligne
- **Les URL de dépôt de Duo's Terminal, Parade, Cobaye et Portfolio** : elles renvoient au profil `github.com/LonerFy`, les autres pointent vers leur dépôt exact
- **Les piles techniques** de TryWeb, LyricStage, Neon Arcade, ORBITAL, Morphogène, GNOSIS, Boudoir, Poem Atelier et Portfolio & CV Generator — TryWeb est traité comme un dépôt privé : ni badge, ni lien de code
- **`cv.pdf`** : déposez le fichier à la racine, le bouton de la section contact pointe déjà dessus
- **`og:image`** : une image de partage 1200 × 630 pour un aperçu illustré sur les réseaux

## Mise en ligne

```bash
git init
git add index.html README.md
git commit -m "portfolio"
git branch -M main
git remote add origin git@github.com:LonerFy/portfolio.git
git push -u origin main
```

Puis **Settings → Pages → Deploy from a branch → main / (root)**.

## Palette

| Rôle | Valeur |
|---|---|
| Fond | `#000000` |
| Texte | `#D9DEE3` / `#B9C0C6` |
| Aplats | `#241A12` cuivre sombre |
| Tracés | `#8C6A44` bronze |
| Accent | `#79F0A8` phosphore, réservé à la sélection et aux lueurs |

En acier, l'accent passe au bleu glacier `#7FD8F5` et le bronze au métal froid `#6F8695`. En clair, aucune couleur n'est employée : `#FFFFFF`, `#000000` et des gris, la hiérarchie passant par la masse, le filet et l'inversion.
