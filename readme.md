# Documentation

## Convention BEM

* B → Block
* E → Element
* M → Modifier

```html
<!-- mainList = Block -->
<ul class="mainList mainList--xmas">
<!-- __item = Element -->
  <li class="mainList__item">
  <!-- __itemLink = Element -->
    <a class="mainList__itemLink mainList__itemLink--isActive" href="/home">Home</a>
  </li>
  <!-- __item = Element -->
  <li class="mainList__item">
  <!-- __itemLink = Element -->
    <a class="mainList__itemLink" href="/home">About</a>
  </li>
  <!-- __item = Element -->
  <li class="mainList__item">
  <!-- __itemLink = Element -->
    <a class="mainList__itemLink" href="/home">Works</a>
  </li>
</ul>
``` 
```scss
.mainList {
    display: flex;
    justify-content: space-between;
    &--xmas {
        background: green;
    }
    &_item {
        list-style: none;
    }
    &__itemLink{
    color: red;
      &--isActive {
        color: white;
      }
    }
}
```
Exemple en CSS du rendu (en plus chiant) :
```css
.mainList {

}
.mainList--xmas {

}
.mainList__item {

}
...
```
## Pseudo attributs
Les pseudo attributs `before` et `after` permettent de créer des noeuds HTML en CSS. Ils sont essentiellement utilisés pour ajouter des ornements, des décorations etc. 
On peut bien entendu faire des animations avec, les positionner par rapport à leur parent (relative / absolute). **Ils doivent obligatoirement avoir un `content : ''`**
afin de s'afficher.

```html
<section class="cover">
    <h1 class="cover__mainTitle">Présentation des pseudo-attributs</h1>
</section>
```
```css
.cover {
    background: #FDFDFD;
    padding: 20px;
    &__mainTitle {
        text-align: center;
        font-size: 24px;
        color: green;
        position: relative;
        &::before, 
        &::after {
            position: absolute;
            content:'';
            display: block;
            width: 50px;
            height: 50px;
            background: green;
            top: 0;
        }
        &::before {
           left: 0;
        }
        &::after {
            right:0;
        }
    }
}
```
## REM, EM, %, VW Sizing


### EM
* Relative à la taille de son parent direct.

```css
.cover {
    font-size: 100%;  /* 100% = 16px */
    &__mainTitle {
        /* 1em = 16px / .8em =/= ~ 12.8px */
        font-size: .8em;
    }
}
```

### REM

* Le REM est basé sur la taille de la racine (soit la balise <html>) qui, par défaut a une valeur de 16px. Afin d'éviter tout calcul, il est nécessaire
de l'écraser en donnant une base de 10px soit 62.5%.
* Le REM est intéressant à utiliser si les media-queries employées sont en rem également. Cela vous permettra de garder des proportions égales lorsqu'on
va redimensionner la page.
* Ses proportions seront également gardées quand l'utilisateur zoomera dans votre page. 

```css
html {
    /* 62.5% = 10px */
    font-size: 62.5%;
}
.mainTitle {
    /* 1.6rem = 16px */
    font-size: 1.6rem;
    /* 32rem = 320px */
    width: 32rem;
}
```
### VW(idth) / VH(eight) Sizing

* Unités relatives à la taille de votre écran (peu importe le device)
* Attention au VH et à son contenu. 100vh = 100vh quoi qu'il arrive.
* VW : très utile pour les interfaces fluides.


## Liens utiles :
* [Caniuse] (https://caniuse.com/) : c'est compatible partout ou pas ?

### FlexBox Grid

```html
<div class="container-fluid">
    <div class="row between-xs">
        <div class="col-xs-6 col-lg-4">
                <h1>Hey Wassup</h1>
                <p>Excepteur minim amet ea elit mollit labore commodo aliquip dolore velit enim elit mollit deserunt.</p>
        </div>
        <div class="col-xs-6 col-lg-4">
                <h1>Je suis la frr</h1>
                <p>Ut eu irure ad irure nostrud excepteur irure eiusmod enim mollit adipisicing. Ea occaecat est consectetur enim amet non culpa.</p>
        </div>
        <div class="col-xs-6 col-lg-4">
                <h1>Lol wsh</h1>
                <p>Sit commodo proident do irure sit elit aliqua veniam mollit. Sunt amet nostrud velit ut occaecat. Mollit nulla enim incididunt incididunt ut consequat Lorem do laborum et velit non ut elit. Commodo aliquip cupidatat eu deserunt quis sunt.
                    Sit irure est elit ipsum velit aliqua duis labore adipisicing culpa ea sunt qui nisi. Dolor eu duis tempor veniam qui exercitation et cupidatat. Minim incididunt non nisi ad amet veniam eiusmod duis exercitation nostrud ex.</p>
        </div>
        <div class="col-xs-6 col-lg-6">
                <h1>yey</h1>
                <p>Cillum reprehenderit sunt ad anim ea. Ex anim mollit do consectetur reprehenderit quis deserunt. Duis esse dolore quis sit tempor laborum voluptate elit do laborum. Sint sunt sit consectetur incididunt Lorem esse ex est enim. Cupidatat
                    id sunt do labore Lorem esse esse quis culpa.</p>
        </div>
        <div class="col-xs-12 col-lg-5 col-lg-offset-1">
                <h1>yesyeyseyesysy</h1>
                <p>Sint incididunt labore amet laborum mollit commodo           voluptate enim aute ut tempor voluptate aute                 exercitation. Ad dolore labore Lorem id duis. Ipsum          veniam ea aliquip reprehenderit commodo occaecat id          reprehenderit sit fugiat eu sunt. Autecillum 
                   consectetur ea in ex. Do ullamco nisi pariatur consequat. Esse enim officia minim elit ad elit. Officia magna aliqua ipsum pariatur dolore est.
                </p>
        </div>
    </div>
</div>
```

### CSS Grid
* Le module CSS Grid layout (modèle de disposition en grille) est un module de la spécification CSS qui permet de créer des mises en page en divisant l'espace d'affichage en régions utilisables par une application ou en définissant des relations de taille, position et d'empilement entre les éléments HTML.

* Comme les tableaux, la grille permet d'aligner des éléments sous forme de colonnes et de lignes mais à la différence des tableaux, la grille n'a pas de structure de contenu. Ainsi, on peut créer de nombreuses mises en page qui n'auraient pas été possibles avec les tableaux. Ainsi, les éléments fils d'un conteneur en grille peuvent être positionnés afin qu'ils se chevauchent ou qu'ils se comportent comme des éléments positionnés.

Exemple :
```html
<div class="wrapper">
  <div class="one">Un</div>
  <div class="two">Deux</div>
  <div class="three">Trois</div>
  <div class="four">Quatre</div>
  <div class="five">Cinq</div>
  <div class="six">Six</div>
</div>
```
```css
.wrapper {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-gap: 10px;
  grid-auto-rows: minmax(100px, auto);
}
.one {
  grid-column: 1 / 3;
  grid-row: 1;
}
.two { 
  grid-column: 2 / 4;
  grid-row: 1 / 3;
}
.three {
  grid-column: 1;
  grid-row: 2 / 5;
}
.four {
  grid-column: 3;
  grid-row: 3;
}
.five {
  grid-column: 2;
  grid-row: 4;
}
.six {
  grid-column: 3;
  grid-row: 4;
}
```
### Flexbox

```css
.container {
  display: flex; /* or inline-flex */
  flex-direction: row | row-reverse | column | column-reverse; 
  /* row:left to right | row-reverse:right to left | column: top to bottom | column-reverse: bottom to top */
  flex-wrap: nowrap | wrap | wrap-reverse;
  /* nowrap: inline | wrap: les items passent chacun en dessous en responsive | wrap-reverse: l'inverse de wrap */
  justify-content: flex-start | flex-end | center | space-between | space-around;
  align-items: flex-start | flex-end | center | baseline | stretch;
  align-content: flex-start | flex-end | center | space-between | space-around | stretch;
}
```
### La syntaxe CSS

* HTML5 est venu avec une bonne et une mauvaise nouvelle. La bonne nouvelle, c'est qu'il est désormais possible d'utiliser n'importe quel caractère dans les identifieurs des attributs class et id. Et la mauvaise nouvelle, c'est que… pas en CSS. Un auteur Belge a dressé la liste des caractères qui ont un sens spécial en CSS et qu'il faut donc échapper : !, ", #, $, %, &, ', (, ), *, +, ,, -, ., /, :, ;, <, =, >, ?, @, [, \, ], ^, `, {, |, } et ~.
* Il reste alors deux caractères de séparation : le trait d'union (-) qu'une règle spéciale permet d'utiliser dans un identifieur sauf en première position, et le underscore (_).

* Toujours donner un nom/une signification à la classe donnée pour se retrouver dans le code. Ex : Cette div est un container qui regroupe plusieurs blocs. Elle fait partie d'une catégorie nommée "Projets". La classe du container s'appelera :

```html
<div class="Projects-container">
    <div></div>
    <div></div>
    <div></div>
</div>
```
### NPM & SCSS
* Dans le dossier (où on retrouve un fichier composer.json etc), faire npm install. Ensuite pour voir le rendu de l'index, entrer dans le dossier src puis faire npm run start.
Dans le dossier styles, on doit retrouver 3 dossiers (components, global et mixins) et un fichier styles.

* Dans le dossier components, on doit retrouver les fichiers scss. (toujours "_" avant le nom)
* Dans le dossier global, on doit retrouver deux fichiers : _reset.scss et _variables.scss. Dans le fichier variables, on retrouve les font-family qui seront utilisés dans les fichiers scss dans components et les breakpoints (responsive).
* Dans le dossier mixins, on retrouve un fichier _forsize.scss où l'on retrouve les media queries de chaque breakpoint. (mobile, desktop, tablet)
* Dans le fichier styles, on recense alors chaque dossier et chaque fichier scss pour que cela fonctionne bien dans les fichiers html.

### Font-face, @import
```css
@font-face {
    font-family: myFirstFont;
    src: url(sansation_light.woff);
}
``` 
A mettre au tout début du fichier css.

```css
@import url('')
```

### Syntaxe position CSS

```css
.container {
/* Valeurs avec un mot-clé */
position: static;
position: relative;
position: absolute;
position: fixed;
position: sticky;

/* Valeurs globales*/
position: inherit;
position: initial;
position: unset;
}
```
* static
Comportement normal (par défaut). L'élément est alors positionné dans le flux avec sa position. Les propriétés top, right, bottom, left et z-index ne s'appliquent pas.
* relative
L'élément est positionné dans le flux normal du document puis décalé, par rapport à lui-même, selon les valeurs fournies par top, right, bottom et left. Le décalage n'a pas d'impact sur la position des éléments. Aussi, l'espace fourni à l'élément sur la page est le même que celui fourni avec static.
Cette valeur crée un nouveau contexte d'empilement lorsque z-index ne vaut pas auto. L'effet de cette valeur n'est pas défini pour les éléments table-*-group, table-row, table-column, table-cell et table-caption.
* absolute
L'élément est retiré du flux normal et aucun espace n'est créé pour l'élément sur la page. Il est ensuite positionné par rapport à son ancêtre le plus proche qui est positionné s'il y en a un ou par rapport au bloc englobant initial sinon. La position finale de l'élément est déterminée par les valeurs de top, right, bottom et left.
Cette valeur crée un nouveau contexte d'empilement lorsque z-index ne vaut pas auto. Les éléments positionnés de façon absolue peuvent avoir des marges, ces marges ne fusionnent pas avec les autres marges.
* fixed
L'élément est retiré du flux normal et aucun espace n'est laissé pour l'élément. L'élément est positionné relativement au bloc englobant initial formé par la zone d'affichage (viewport), sauf si un des ancêtres a une propriété transform, perspective ou filter qui est différente de none (voir la spécification sur les transformations CSS) ; dans ce cas, c'est l'élément ancêtre qui joue le rôle de bloc englobant.  Cela empêche le défilement lorsque la page est parcourue (ou lors de l'impression, le positionne à cette position fixe pour chaque page). Cette valeur crée toujours un nouveau contexte d'empilement. Certains incohérences existent entre les navigateurs quant au rôle de perspective et filter pour la définition du bloc englobant. La valeur finale de l'élément est déterminée par les valeurs de top, right, bottom et left.
Cette valeur crée toujours un nouveau contexte d'empilement. Pour les documents imprimés, cela se traduit par le placement de l'élément au même endroit pour chacune des pages.
* sticky 
La position de la boîte est calculée en fonction du flux normal du document. Ensuite, la boîte est décalée par rapport à son ancêtre de défilement le plus proche et par rapport à son bloc englobant selon les valeurs de top, right, bottom et left. Dans tous les cas, y compris avec les éléments table, cela n'affecte pas la position des autres éléments.
Cette valeur entraîne toujours la création d'un nouveau contexte d'empilement. On notera qu'un tel élément « adhèrera » à l'ancêtre le plus proche qui dispose d'un mécanisme de défilement (c'est-à-dire quand overflow vaut hidden, scroll, auto ou overlay) même si cet ancêtre n'est pas nécessairement l'ancêtre de défilement le plus proche : cette valeur ne fonctionnera pas dans un élément pour lequel la propriété vaut overflow: hidden ou auto