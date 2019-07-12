# Paywall by ViewPay

Ce guide a pour objectif de vous guider dans la mise en place du widget JS Paywall de ViewPay dans votre site web.

Pour rappel, Viewpay est une solution de micro-paiement par l'attention publicitaire, qui permet à l'utilisateur de débloquer un contenu premium en regardant une publicité. Le Paywall de ViewPay a été fait pour répondre aux besoins d'éditeurs n'ayant pas de Paywall existant mais souhaitant intégrer ViewPay.

Voici un exemple de déblocage d'article avec Viewpay : 

![sample](https://github.com/TechViewpay/ViewPay-iOS/blob/master/DocImages/parcours_vp_mobile3.png?raw=true)

## Chargement du Javascript
```html
<script type="text/javascript" src="https://www.pmur.org/Prod/ViewPayWall.js"></script>
```
Le fichier ViewPayWall.js est le seul fichier nécessaire à appeler, celui-ci fera ensuite le travail afin d'appeler les éléments nécessaires pour un moment donné.
Ces fichiers sont installés sur notre CDN afin de vous garantir d'avoir toujours la dernière version.

NB: Il faut placer le script le plus haut possible dans la page afin d’optimiser son temps de chargement.

## Fonctions Javascript et lancement du Paywall

Les fonctions JS vont permettre au paywall de s'afficher correctement et de faire le parcours nécessaire à celui-ci.
```
<script> 
	var payWall = null;
	function VPinitVideo(){
		payWall = new ViewPayWall({
			site_id: '//ID', //Remplacer le commentaire par l'ID fourni par l'administrateur ViewPay
			load_callback:existAds, // Voir Doc ViewPay HTML
			noads_callback: noAds, // Voir Doc ViewPay HTML
			complete_callback:completeAds, // Voir Doc ViewPay HTML
			close_callback:closeAds, // Voir Doc ViewPay HTML
			play_callback : play, 
			display_paywall  : true //True : Affiche le paywall, False : Pas de Paywall
		});
	}		
	// Voir Doc ViewPay HTML
	function VPexistAds(){
		console.log('existAds'); 
		$("#lien-voir-content").css("display","block");
	}
	// Voir Doc ViewPay HTML
	function VPnoAds(){
		console.log('noAds');
		$("#lien-error").css("display","block");
	}
    
	// Voir Doc ViewPay HTML
    	function VPcompleteAds(){
		console.log('completeAds');
		payWall.showText(); //Débloquage article
	}
    
	// Voir Doc ViewPay HTML
	function VPcloseAds(){
		console.log('closeAds');
	}
	
	function VPplay(){
		console.log('play');
	}
</script>
```
Le callback "display_paywall" permet d'afficher ou non le paywall en fonction de votre propre stratégie. 
Si c'est un article payant, j'affiche le paywall (true).
L'article est gratuit, je n'affiche pas le Paywall (false).

## Nom de div pour les différentes actions

Chacun des divs possèdent son propre CSS qui peut-être modifié lors de l'intégration du Paywall à l'aide de votre propre fichier de CSS, ou directement en inline

```
<p class="ViewPay_Opacity"></p>
```
Cette classe contient l'introduction de l'article permettant à l'utilisateur de commencer sa lecture afin de lui donner envie de continuer puis de lui montrer le paywall.
Cette div permet de cacher l'introduction au fur et à mesure de l'arrivée du Paywall grâce à du CSS.

```
<div id="ViewPay_ReadPC"></div>
```
Cet ID permet d'afficher le pourcentage de lecture restant par rapport à la totalité de l'article.
"Il vous reste 95% de l'article à lire"
C'est à partir de celle-ci que nous allons afficher tout le contenu du Paywall.
Nous pouvons donc hériter de CSS de div parents.
Le Paywall possède des outils dans le BO à configurer dans votre compte, nous l'étoffons de jour en jour afin de satisfaire un maximum de besoin.

```
<div id="ViewPay_Article">Lorem ipsum </div>
```
Cet ID permettra de cacher l'article à l'aide de JS.
Si le JS est désactivé chez l'utilisateur, nous utilisons alors du CSS.

Les options suivantes du Paywall en BO sont actuellement :
- ViewPay : Débloquage de l'article par une attention publicitaire
- Abonnement : Redirection vers une page définie dans votre compte.
