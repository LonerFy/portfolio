# Portfolio — AMOUSSOU-GUENOU Donald

Portfolio personnel dans **un seul fichier statique**, bilingue français/anglais. Aucune bibliothèque, aucun build : `index.html` contient l'écran d'entrée et le portfolio. Seules ressources externes : les polices Google Fonts (avec repli système si elles ne chargent pas) et `og.png`, l'image d'aperçu pour les réseaux.

Adresse une fois publié : **https://lonerfy.github.io/portfolio/**

## L'écran d'entrée

Écran noir, une phrase seule — « Approchez. » — puis le rideau se lève : le portrait occupe toute la hauteur à droite et déborde du cadre, le menu tient la gauche en grandes lames obliques, les compteurs en bas. Choisir une entrée fait basculer vers la section correspondante du portfolio ; le bouton *accueil*, en haut à droite du portfolio, ramène à l'écran d'entrée. Une adresse directe comme `#projets` saute l'entrée et ouvre la section.

Le portrait est un nuage de particules sur canvas qui compose successivement quatre photos. Entre deux photos les points se dispersent puis se rassemblent. Ils fuient le curseur, un clic sur le cadre passe à la photo suivante, et le cycle tourne seul toutes les sept secondes. Survoler une entrée du menu change la légende sous le portrait.

Les nuages sont **précalculés et intégrés au fichier** : chaque point tient en quatre caractères en base 36 qui encodent sa position dans une grille de 300 × 380 et son niveau de clarté de 0 à 3. Aucune image n'est chargée au moment de l'affichage, donc rien à héberger et rien qui puisse échouer. Les données sont dans le tableau `PORTRAITS`, en tête du script.

## Le portfolio

- Cinq sections : accueil, profil, projets, parcours, contact
- Section projets en deux temps : une **sélection** (les projets marqués `vedette:true`), puis un bouton **Voir les N projets** qui déplie la liste complète avec des **filtres** — jeux, applications, outils, sites et expériences
- Fiche détaillée par projet, badge « démo en ligne » et badge « dépôt public »
- **Aperçus** : une capture de chaque démo (dossier `apercus/`, WebP 480 × 300, environ 6 Ko chacune), en noir et blanc au repos et en couleur au survol, chargée seulement quand la carte approche de l'écran
- **Sur écran tactile**, la tuile qui passe au milieu de l'écran s'active seule, comme au survol : elle passe en noir, gigote et son aperçu reprend ses couleurs
- Sur l'écran d'entrée, la tuile choisie et les petites plaques numérotées gigotent comme les onglets du portfolio
- **Compteurs calculés** : le nombre de projets et de démos (écran d'entrée, accroche, légendes) se déduit du tableau `PROJETS`, rien à mettre à jour à la main
- Lien **CV** : `cv.pdf` (français) ou `cv-en.pdf` (anglais) selon la langue du site ; le lien se masque tout seul si le fichier manque
- Bascule **FR / EN** sur tout le contenu, langue devinée du navigateur au premier chargement
- Adresses directes : `#projets` ouvre la section, `#projets/snake` ouvre la fiche (la liste complète se déplie si le projet n'est pas dans la sélection)
- Navigation clavier : `↑` `↓` changent de section, `1` à `5` en accès direct, `Échap` ferme
- Trois ambiances au même bouton, chacune avec son identité :
  - **clair** — blanc pur, noir pur, aucune teinte : l'ambiance d'ouverture
  - **cuivre** — noir, argent, cuivre oxydé, accent vert phosphore
  - **acier** — noir bleuté, métal froid, accent glacier
- Le site s'ouvre en **mode clair**, animations actives. Le bouton **animations / sobre** permet de tout couper ; le bouton d'ambiance fait défiler clair, cuivre, acier
- Mise en page d'impression propre : `Ctrl+P` donne un document noir sur blanc, toutes sections dépliées
- Métadonnées de partage avec image `og.png` (1200 × 630), favicon vectorielle intégrée

## Modifier le contenu

Tout est en haut du `<script>`. Chaque texte est un objet `{fr, en}`.

| Tableau | Ce qu'il alimente |
|---|---|
| `PORTRAITS` | les nuages de points du portrait |
| `I` | libellés d'interface, titres, accroche, menu d'entrée et ses légendes |
| `PROJETS` | la grille et les fiches |
| `COMPETENCES` | les sept cartes du profil |
| `PARCOURS` | la chronologie |
| `LIENS` | la section contact |

Un projet se déclare ainsi :

```js
{nom:"Snake", vedette:true, tag:{fr:"jeu",en:"game"},
 public:true, lien:GITHUB+"/Snake",
 demo:"https://lonerfy.github.io/Snake/",
 resume:{fr:"Une phrase sur la carte.", en:"One line on the card."},
 texte:{fr:"Le paragraphe de la fiche.", en:"The detail paragraph."},
 pile:["TypeScript"]}
```

`public:true` affiche le badge « dépôt public » et le bouton *Voir le code*. `demo` ajoute le badge « démo en ligne » et le bouton *Ouvrir la démo*. `vedette:true` place le projet dans la sélection visible d'emblée. `apercu:true` affiche l'image `apercus/<nom-en-minuscules>.webp` (par exemple `apercus/la-crypte.webp`). Tous trois sont facultatifs. L'ordre du tableau est l'ordre d'affichage.

Le filtre se déduit du `tag` : `jeu` → Jeux ; `application`, `web app` → Applications ; `outil`, `écriture` → Outils ; `site`, `visuel`, `expérience` → Sites et expériences.

## À compléter

- **Les piles techniques** de TryWeb, GNOSIS et Poem Atelier (dépôts privés)

## Mise en ligne

```bash
git init
git add index.html README.md og.png apercus cv.pdf cv-en.pdf
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
