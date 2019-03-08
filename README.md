# Paywall by ViewPay

Ce guide a pour objectif de vous guider dans la mise en place du widget JS Paywall de ViewPay dans votre site web.

Pour rappel, Viewpay est une solution de micro-paiement par l'attention publicitaire, qui permet à l'utilisateur de débloquer un contenu premium en regardant une publicité. Le Paywall de ViewPay a été fait pour répondre aux besoins d'éditeurs n'ayant pas de Paywall existant mais souhaitant intégrer ViewPay. Cependant, Viewpay a pour vocation d'être une alternative à d'autres options pour débloquer un contenu premium, et ne doit pas être installé comme seule option d'un paywall.

Voici un exemple de déblocage d'article avec Viewpay : 

![sample](https://github.com/TechViewpay/ViewPay-iOS/blob/master/DocImages/parcours_vp_mobile3.png?raw=true)

## Chargement du Javascript
```html
<script type="text/javascript" src="https://www.pmur.org/Prod/ViewPayWall.js"></script>
```
Le fichier ViewPayWall.js est le seul fichier nécessaire à appeler, celui-ci fera ensuite le travail nécessaire à appeler les éléments nécessaires pour un moment donné.
Ces fichiers sont installés sur notre CDN afin de vous garantir d'avoir toujours la dernière version.

NB: Il faut placer le script le plus haut possible dans la page afin d’optimiser son temps de chargement.

## Nom de div pour les différentes actions

Chacun des divs possèdent son propre CSS qui peut-être modifié lors de l'intégration du Paywall.

```
<p class="ViewPay_Opacity"></p>
```
Cette classe contient l'introduction de l'article permettant à l'utilisateur de commencer sa lecture afin de lui donner envie puis de lui montrer le paywall.
Cette div permet de cacher l'introduction au fur et à mesure de l'arrivée du Paywall grâce à du CSS.

```
<div id="ViewPay_ReadPC"></div>
```
Cet ID permet d'afficher le pourcentage de lecture restant par rapport à la totalité de l'article.
"Il vous reste 95% de l'article à lire"

```
<div id="ViewPay_Article">Lorem ipsum </div>
```
Cet ID permettra de cacher l'article à l'aide de JS chez nous, si le JS est désactivé chez l'utilisateur, nous utilisons alors du CSS.



## Etape 2
```html
code
```
text
