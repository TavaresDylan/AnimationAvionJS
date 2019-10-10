# Challenge  Reverse-engineering :

Faire un tutoriel d'animation sur la base de "annimate" (Repo de julien)

# Préparation du projet :

## Les ressources :

Nous allons utiliser différentes ressources pour nous aider à reproduire cette animation.
Tout d'abord nous allons regarder dans les fichiers du repo "annimate" pour voir ce qui est utiliser , nous pouvons lister :
En physique (présent dans les dossiers du site)
- Une image au format png
- Un fichier App.js en javascript , notre coeur de l'application
- Un fichier pour le style du site style.css
En virtuel (importation par CDN)
- Une police d'écriture Google Font : `<link href="https://fonts.googleapis.com/css?family=Roboto&display=swap" rel="stylesheet">`
- Un script ScrollMagic [Ressources](https://scrollmagic.io/)
- Un script addIndicators [Ressources](https://scrollmagic.io/docs/debug.addIndicators.html)
- Un script animation [Ressources](https://greensock.com/gsap/)
- un script TweenLite [Ressources](https://greensock.com/tweenlite/)
- un script TimelineLite [Ressources](https://greensock.com/timelinelite/)
- un script CSSPlugin [Ressources](https://greensock.com/cssplugin/)
- un script Bezier plugin [Ressources](https://greensock.com/bezierplugin-js/)
```HTML
<script src="https://cdnjs.cloudflare.com/ajax/libs/ScrollMagic/2.0.7/ScrollMagic.min.js"
        integrity="sha256-2p2tRZlPowp3P/04Pw2rqVCSbhyV/IB7ZEVUglrDS/c=" crossorigin="anonymous"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/ScrollMagic/2.0.7/plugins/debug.addIndicators.js"
        integrity="sha256-31FC/OT6XpfjAhj9FuXjw5/wPXXawCAjJQ29E23/XPk=" crossorigin="anonymous"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/ScrollMagic/2.0.7/plugins/animation.gsap.min.js"
        integrity="sha256-+9YNuItWuR4sbqeaNiJOxG0BvptYz4fbUXbIZoH5Jwo=" crossorigin="anonymous"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/2.1.3/TweenLite.min.js"
        integrity="sha256-VV47uJSoHZUeiBcCs3FcBOQLMn++yeG/zqZvaUkvGZM=" crossorigin="anonymous"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/2.1.3/TimelineLite.min.js"
        integrity="sha256-nuhNsfXzBFR6G1lKP8bK77dakkQDqdHcQ4OCFZvk6Qo=" crossorigin="anonymous"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/2.1.3/plugins/CSSPlugin.min.js"
        integrity="sha256-LBjlnpPrM6Aig8LDFc9PJctPHLGUc6RaUvnmXE4hV5Y=" crossorigin="anonymous"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/2.1.3/plugins/BezierPlugin.min.js"
        integrity="sha256-5jxCMRC1PYU02qJn+fj+DPuxcQZCh0DR8GRwi4iKoRc=" crossorigin="anonymous"></script>
```

## Construction de la structure :
Créer un dossier nommé : "AnimationJS" par exemple.
Rien de bien compliqué jusqu'ici , il nous faudra une architecture comprenant:
- Un fichier index.html
- Un fichier App.js
- Un fichier style.css
- Un fichier image.png

## Explication de l'animation :

L'animation est faite à l'aide des scripts que nous allons importer dans le index.html
Lorsque l'utilisateur scroll (défile l'écran) une animation ce lance à chaque niveau du scroll de la page et fait bouger un élément (l'image png)
[Voir ici](https://scrollmagic.io/)

# Départ du tuto :

## HTML :

Dans le fichier index.html nous allons importer et lier toutes les ressources et les fichier dont nous avons besoin.
Une fois cela fait il nous reste plus qu'as créer quelques balises :
- Un header avec un titre h1
- Une section avec une image
- Un footer avec un titre h1

Ce qui donnera ceci :
```HTML
<!DOCTYPE html>
<!-- PAGE LANGUAGE -->
<html lang="fr">

<head>
    <!-- Characters Encoder -->
    <meta charset="UTF-8">
    <!-- RESPONSIVE VIEWPORT -->
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <!-- INTERNET EXPLORER COMPATIBILITY -->
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <!-- TAB TITLE -->
    <title>AnimationJS</title>
    <!-- STYLESHEET -->
    <link rel="stylesheet" href="style.css">
    <!-- GOOGLE FONT CDN -->
    <link href="https://fonts.googleapis.com/css?family=Roboto&display=swap" rel="stylesheet">
</head>

<body>
    <header>
        <!-- TITLE ON PAGE -->
        <h1>Scroll Annimation</h1>
    </header>
    <!-- SECTION WITH IMAGE -->
    <section class="animation">
        <img class="paper-plane" src="avion.png" alt="" srcset="">
    </section>
    <!-- FOOTER -->
    <footer>
        <h1>cool</h1>
    </footer>
    <!-- SCRIPTS JAVASCRIPT CDN -->
    <script src="https://cdnjs.cloudflare.com/ajax/libs/ScrollMagic/2.0.7/ScrollMagic.min.js"
        integrity="sha256-2p2tRZlPowp3P/04Pw2rqVCSbhyV/IB7ZEVUglrDS/c=" crossorigin="anonymous"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/ScrollMagic/2.0.7/plugins/debug.addIndicators.js"
        integrity="sha256-31FC/OT6XpfjAhj9FuXjw5/wPXXawCAjJQ29E23/XPk=" crossorigin="anonymous"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/ScrollMagic/2.0.7/plugins/animation.gsap.min.js"
        integrity="sha256-+9YNuItWuR4sbqeaNiJOxG0BvptYz4fbUXbIZoH5Jwo=" crossorigin="anonymous"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/2.1.3/TweenLite.min.js"
        integrity="sha256-VV47uJSoHZUeiBcCs3FcBOQLMn++yeG/zqZvaUkvGZM=" crossorigin="anonymous"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/2.1.3/TimelineLite.min.js"
        integrity="sha256-nuhNsfXzBFR6G1lKP8bK77dakkQDqdHcQ4OCFZvk6Qo=" crossorigin="anonymous"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/2.1.3/plugins/CSSPlugin.min.js"
        integrity="sha256-LBjlnpPrM6Aig8LDFc9PJctPHLGUc6RaUvnmXE4hV5Y=" crossorigin="anonymous"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/2.1.3/plugins/BezierPlugin.min.js"
        integrity="sha256-5jxCMRC1PYU02qJn+fj+DPuxcQZCh0DR8GRwi4iKoRc=" crossorigin="anonymous"></script>
    <script src="App.js"></script>

</body>

</html>
```

## CSS :

Tout d'abord nous allons réinitialisé notre style avec ce bout de code CSS:
```CSS
*{margin: 0; // Initialise les marges extérieures à 0
    padding: 0; // Initialise les marges intérieures à 0
    box-sizing: border-box; // Inclusion des bordures 
}
```
Ensuite nous allons définir le style du texte dans le header et le footer:
```CSS
header, footer{
    height: 100vh; // Vh signifiant viewport height / unitée responsive
    display: flex; // Utilisation du module flexbox
    justify-content: center; // Alignement horizontal flex au centre
    align-items: center; // Alignement vertical flex au centre
    font-family: 'Roboto', Arial, sans-serif; // Définition de la police de caratère Roboto: police perso importée
}
```
La taille du text dans le h1 du header:
```CSS
header h1{
    font-size: 60px; // Taille de Police
}
```
le fond de la section où ce trouvera l'image ainsi que la position de départ de la dite image
```CSS
.animation{
    height: 100vh; // Vh signifiant viewport height / unitée responsive
    background-image: linear-gradient(45deg, #ff9a9e 0%, #fad0c4 99%, #fad0c4 100%); // Dégradé d'arrière plan
    position: relative;
    overflow: hidden; // Cache le contenu s'il est ammener à dépasser de ça boite
}
```
Pour finir nous définirons la position de l'image
```CSS
.paper-plane{
    height: 100px;
    position: relative;
    top: 50%;
    left: 0%;
}
```

## Javascript

Dans la fichier App.js nous allons pouvoir commencé à animer notre bel avion en papier.

On commence par définir une constante qui se nommera flightPath (littéralement chemin d'envole), cette constante contiendra un tableau js dans lequel on retrouvera les positions de l'image lors du scroll. On indique également que l'on souhaite que notre image effectue une rotation de manière automatique.

```JS
const flightPath = {
    curviness: 1.25,
    autoRotate: true, // Auto-rotation : activé
    values: [
        { x: 100, y: -20 },
        { x: 300, y: 10 },
        { x: 500, y: 100 },
        { x: 750, y: -100 },
        { x: 350, y: -50 },
        { x: 600, y: 100 },
        { x: 800, y: 0 },
        { x: window.innerWidth, y: -250 }
    ] // Valeur du chemin de vol
}
```
On déclare une nouvelle constante qui se nommera tween et qui appelera un nouvel objet TimelineLite() depuis le CDN.
[=> Voir la doc <=](https://greensock.com/timelinelite/)
```JS
const tween = new TimelineLite();

tween.add(
    TweenLite.to(".paper-plane", 1, {
        bezier: flightPath,
        ease: Power1.easeInOut
    })
);
```
On déclare une nouvelle constante qui se nommera controller et qui appelera un nouvel objet ScrollMagic.Controller() depuis le CDN.
```JS
const controller = new ScrollMagic.Controller();
```
On déclare une nouvelle constante qui se nommera scene et qui appelera un nouvel objet ScrollMagic.Scene() depuis le CDN qui prendra en paramètres la classe de l'element visé la durée en microsecondes et la vitesse d'animation.
```JS
const scene = new ScrollMagic.Scene({
    // CLasse de l'élément visé
    triggerElement: '.animation',
    // Durée de l'animation en ms
    duration: 500,
    triggerHook: 0.4
})
    .setTween(tween)
    //.addIndicators() //optional
    .addTo(controller);
```