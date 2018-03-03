# SEO basics and more

Voici les grandes lignes des choses à prévoir avant et pendant le développement de vos tâches finales. Tous ces points, et de nombreux autres, seront détaillés lors de l'atelier du 16 mars.

## Nom du projet et NDD

Une fois que vous avez trouvé la thématique de votre projet, vous devez vous trouver un nom et nom de domaine (NDD) qui va bien. Deux options:

* nom de domaine premium
* marque sympa

* trouver des mots clés : http://adwords.google.com/keywordplanner / https://trends.google.com/trends/

Ex: pour un site de concert: concert.info OU viagogo.com et PAS place-billet-concert.com qui sent le spam

Ex2: si vous ne ciblez que marseille, concert-marseille.com est OK.

## Avant de commencer

Tout comme vous faites un schéma pour visualiser votre développement ou vos div en css, le SEO doit se dessiner. Vous trouverez plus bas l'ensemble des éléments qui rendent une page attractive pour un moteur de recherche. Nombre de ces éléments sont directement associés à des entrées de votre base de données. Dans le cas d'un produit par exemple, il faudra un titre, une description, une image, un prix, une URL, de quoi faire du spin ... autant d'éléments à intégrer et prévoir pour essayer d'avoir tout bon dès le premier "rails g".

## On lance le dev!

Développez sur un heroku avant de basculer sur votre NDD. Tant que le site n'est pas terminé et officiellement lancé vous DEVEZ mettre cette balise dans le <head> (même sur heroku):

<META NAME="robots" CONTENT="noindex,nofollow">

Ceci peut être géré via le fichier robots.txt http://www.robotstxt.org/robotstxt.html

Cette balise a pour but d'empêcher l'indexation de votre site et donc de votre fake content et de vos pages pleines de bug. Quand vous êtes OK, il suffit de la retirer.

* Dans votre code, utilisez autant que possible le balisage http://schema.org/ et testez si c'est OK avec https://search.google.com/structured-data/testing-tool/u/0/
* utilisez un CDN pour toutes les ressources statiques: images, css, js https://devcenter.heroku.com/articles/fastly

## URL

* Protocole HTTPS est un vrai plus en SEO https://example.com
* dossiers: https://example.com/dossier/
* pages / produit : https://example.com/dossier/page.html
* essayez de ne pas aller au delà d'un niveau de dossiers
* URL rewriting OBLIGATOIRE :
    * MAL :   https://example.com/produit?cat=2&item=123
    * BIEN :  https://example.com/echarpe/echarpe-en-laine-dacquay.html

## Head:

Le contenu du <head> est ce que les moteurs voient en premier sur votre site. Voilà ce qu'il doit contenir:

Données communes à chaque page et langue
* doctype
* html itemtype schema.org + lang
* charset
* minify css et un seul fichier
* min js et un seul fichier si doit apparaître en header
* nettoyage des commentaires

Données propres à chaque page
* title
* meta desc
* open graph
* icone .ico
* rel canonical

## Content

* pas de style inline
* un seul H1, puis des H2 si besoin, qui contiennent des H3 et PAS H1 puis des H4 ...
* fil d'Ariane (Breadcrumbs si tu veux faire le malin) balisés http://schema.org/BreadcrumbList
* spécification de la taille des images
* optimisation des images (alt, taille suffisante et poids optimisé, taille spécifiée)
* optimisation des liens (title, alt)
* optimisation du texte (balisage, structure, longueur ...) + content spinning
* balisage schema.org

## Content Spinning

Le content spinning, c'est la génération automatique de phrases.

Exemple de spin de concert pour les Rolling Stones

"Le concert des Rolling Stones se tiendra le 26 juin 2018 au stade Vélodrome de Marseille à partir de 19h. Le prix des places va de 80€ à 240€.Les places pour les Rolling Stones seront en vente à partir du 16 mars."

Le même pour Muse

"Le concert de Muse se tiendra le 26 juin 2018 au stade Vélodrome de Marseille à partir de 19h. Le prix des places va de 80€ à 240€.Les places pour Muse seront en vente à partir du 16 mars."

Vous pouvez facilement voir que nous avons besoin de plus d'éléments en base pour un groupe, une salle et une ville que ce qui parait évident.
Ainsi, pour les artistes, on aura besoin de:
* nom du groupe
* nombre: singulier / pluriel
* prefixe de : de / des / d' / de la ...
* prefixe le : le / les / la ...
* ....
Idem pour les salles, les villes

Cette stratégie de spin permet, outre le contenu, de créer des Title et Meta desc de qualité, ce qui est fortement apprécié des moteurs.

## Juste avant de lancer le site

* création d'un sitemap
* mise en place des expires header
* utilsez un outil comme https://www.seoptimer.com/ pour voir si vous avez loupé un truc
* améliorez la vitesse de chargement de votre site en suivant les recommandations de https://gtmetrix.com/ et https://developers.google.com/speed/pagespeed/insights/

## Juste après le lancement

* déclarez votre site sur https://www.google.com/webmasters/tools/ qui permet à Google de vous alerter en cas de pb, mais aussi d'avoir qq stats sur votre positionnement, l'état de votre référencement
* intégrez un outil stat comme https://analytics.google.com/analytics/web/

Nous aborderons d'autres points et outils lors de la conf du 16, RDV sur slack #Tools-SEO-SMO, je tente des faire des maj ASAP pour la partie SMO, mais vous avez déjà de quoi vous mettre dans le bain avec ce doc.
