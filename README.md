# Paywall by ViewPay

Ce guide a pour objectif de vous guider dans la mise en place du widget JS Paywall de ViewPay dans votre site web.

Pour rappel, Viewpay est une solution de micro-paiement par l'attention publicitaire, qui permet à l'utilisateur de débloquer un contenu premium en regardant une publicité. Le Paywall de ViewPay a été fait pour répondre aux besoins d'éditeurs n'ayant pas de Paywall existant mais souhaitant intégrer ViewPay. Cependant, Viewpay a pour vocation d'être une alternative à d'autres options pour débloquer un contenu premium, et ne doit pas être installé comme seule option d'un paywall.

Voici un exemple de déblocage d'article avec Viewpay : 

![sample](https://github.com/TechViewpay/ViewPay-iOS/blob/master/DocImages/parcours_vp_mobile3.png?raw=true)

## Chargement du Javascript
```html
<script type="text/javascript" src="https://www.pmur.org/Prod/ViewPayWall.js"></script>
```
Le fichier ViewPayWall.js est le seul fichier qui doit être chargé dans la page qui va accueillir le paywall (page affichant le paywall). Ce fichier est servi par notre CDN, pour vous garantir d'avoir toujours la dernière version.

NB: Il faut placer le script le plus haut possible dans la page afin d’optimiser son temps de chargement.

## Nom de div pour les différentes actions

```
<p class="ViewPay_Opacity"></p>
```
Permet de cacher le texte au fur et à mesure de l'arrivée du Paywall.
C'est la div contenant l'introduction de l'article

```
<div id="ViewPay_ReadPC"></div>
```
Permet d'afficher le pourcentage de lecture restante sur la totalité de l'article
"Il vous reste 95% de l'article à lire"

```
<div id="ViewPay_Article">Lorem ipsum </div>
```
Voici la div contenant la partie de l'article bloqué


## Etape 2
```html
code
```
text
