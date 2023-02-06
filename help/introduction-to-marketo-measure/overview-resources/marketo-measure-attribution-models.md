---
unique-page-id: 18874568
description: Modèles d’attribution Marketo Measure - Marketo Measure - Documentation du produit
title: Modèles d’attribution Marketo Measure
exl-id: d8f76f29-e7c9-4b2d-b599-e80fd93c4687
source-git-commit: 0aa263053aa8dd804b03a67ab446dc0cda3850c5
workflow-type: tm+mt
source-wordcount: '734'
ht-degree: 2%

---

# Modèles d’attribution Marketo Measure {#marketo-measure-attribution-models}

Marketo Measure offre six types de modèles d’attribution :

* First Touch
* Création de prospects
* En U
* En W
* Chemin complet
* Modèle personnalisé

Ces modèles varient en complexité. Première touche et création de pistes sont nos modèles simples à une seule touche. Les quatre autres sont nos modèles multi-touch les plus complexes. La structure des modèles d’attribution de Marketo Measure reflète les quatre principaux points de contact qui se produisent dans le parcours client :

* First Touch (FT)
* Création de lead (LC)
* Création d’une opportunité (OC)
* Offre à perte fermée (CW)

![](assets/1-1.png)

Dans le **modèles tactiles simples**, le crédit d’attribution n’est attribué qu’à un point de contact de jalon, d’où le nom &quot;touche unique&quot;.
Dans le **modèles multi-touch**, la plupart du crédit d’attribution est attribué à deux points de contact de jalon ou plus. Le crédit restant est attribué aux points de contact qui se produisent entre les points de contact du jalon.

Les sections suivantes couvrent chaque modèle d’attribution et la manière dont le crédit d’attribution est attribué.

## Modèles tactiles uniques {#single-touch-models}

**Modèle Première touche**

Le modèle Première touche se concentre uniquement sur la toute première interaction qu’un prospect a avec votre entreprise. Ce modèle attribue 100 % du crédit d’attribution à la première fois que l’prospect a pris connaissance de votre société, la Première touche (FT).

Dites que Kate visite www.adobe.com pour la première fois via une publicité AdWords et consulte un livre blanc. Le canal Adwords recevra 100 % du crédit d’attribution de cette opportunité.

![](assets/2.png)

**Modèle de création de piste**

Le modèle Création de piste attribue 100 % du crédit d’attribution au point de contact LC lorsqu’un prospect fournit ses coordonnées et devient une piste.

Dans la suite de l’exemple précédent, après la première visite de Kate à www.adobe.com par Adwords, Austin se rend sur le site via un article de Linkedin. Austin remplit un formulaire et devient un Lead. Dans ce modèle, Linkedin recevra 100 % du crédit d’attribution.

![](assets/3.png)

## Modèles tactiles multiples {#multi-touch-models}

Les modèles multi-touch sont utilisés pour des cycles de vente plus longs et plus complexes. Ces modèles sont particulièrement utiles si plusieurs personnes d’un compte/d’une société sont impliquées dans le parcours de l’acheteur.

**Modèle en forme de U**

Le modèle en forme de U se concentre sur les points de contact FT et LC. Dans ce modèle, les points de contact FT et LC reçoivent chacun 50 % du crédit de recettes.

La première visite de Kate à www.adobe.com par le biais d’une publicité AdWords recevra 50 % du crédit d’attribution. Les 50% restants seraient attribués au billet Linkedin qui a conduit Austin à remplir un formulaire et à devenir une piste.

![](assets/4.png)

**Modèle en forme de W**

Trois des points de contact de jalon sont inclus dans le modèle en forme de W. Dans ce modèle, les points de contact FT, LC et OC se voient attribuer chacun 30 % du crédit d’attribution. Les 10 % restants sont attribués proportionnellement à tout point de contact intermédiaire qui se produit entre les trois points de contact de jalon.

Kate et Austin mentionnent Marketo Measure à leur collègue, Hillary. Elle trouve un élément de contenu à travers une recherche Google et remplit un formulaire. Plus tard, Austin reçoit un e-mail d&#39;inscription à un webinaire et remplit le formulaire d&#39;inscription sur le site web. Kate a une conversation avec un représentant commercial au sujet du produit Marketo Measure.

Hillary reçoit un e-mail avec un lien vers la page des tarifs et visite la page. Une opportunité est ensuite créée pour leur compte. La visite web d’Hillary sur la page de tarification reçoit du crédit pour la création d’opportunités, car il s’agit de l’interaction marketing la plus proche de la date de création d’opportunités. Chacun des points de contact de jalon se voit attribuer 30 % du crédit d’attribution et les points de contact intermédiaires se voient attribuer les 10 % restants.

![](assets/5.png)

**Modèle de chemin complet**

Le modèle de chemin complet comprend les quatre points de contact de jalon. Le FT, la LC, l’OC et la CW reçoivent chacun 22,5 % du crédit de recettes, et les 10 % restants sont répartis à parts égales entre les touches intermédiaires.

Après la création de l&#39;opportunité, Kate, Austin et Hillary décident de présenter Marketo Measure à leur CMO, Elizabeth. Elizabeth assiste à une conférence où Marketo Measure accueille un événement. Kate voit un article de Linkedin sur une étude de cas et remplit un formulaire pour télécharger le contenu. Elizabeth assiste à un dîner de vente organisé par Marketo Measure. Après le dîner, elle décide d’acheter Marketo Measure et devient cliente. Dans ce scénario, le dîner de vente se verrait attribuer 22,5 % du crédit de recettes de l’opération close. Les points de contact FT, LC et OC reçoivent chacun 22,5 % du crédit. Les points de contact intermédiaires se voient attribuer les 10 % restants du crédit de recettes.

![](assets/6.png)

**Modèle d’attribution personnalisé**

Marketo Measure propose également un modèle d’attribution personnalisée qui permet aux utilisateurs de choisir les points de contact ou les étapes personnalisées à inclure dans leur modèle. En outre, les utilisateurs peuvent contrôler le pourcentage du crédit d’attribution attribué à ces points de contact et étapes.
