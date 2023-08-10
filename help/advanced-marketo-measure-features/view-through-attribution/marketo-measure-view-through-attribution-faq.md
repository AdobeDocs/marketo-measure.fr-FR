---
unique-page-id: 18874652
description: "[!DNL Marketo Measure] FAQ sur l’attribution d’affichages publicitaires - [!DNL Marketo Measure] - Documentation du produit"
title: "[!DNL Marketo Measure] FAQ sur l’attribution d’affichages publicitaires"
exl-id: d20e88f3-3ff8-4381-a4b8-6862798caa74
feature: Attribution
source-git-commit: 8ac315e7c4110d14811e77ef0586bd663ea1f8ab
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 14%

---

# Questions fréquentes sur l’attribution de visionnage moyen dans [!DNL Marketo Measure] {#marketo-measure-view-through-attribution-faq}

## Qu’est-ce que l’attribution d’affichage publicitaire ? {#what-is-view-through-attribution}

La variable [!DNL Marketo Measure] La fonction d’attribution d’affichages publicitaires offre la possibilité d’inclure des impressions publicitaires dans le modèle d’attribution.

## Pourquoi l’attribution d’affichage publicitaire est-elle importante ? {#why-is-view-through-attribution-important}

Historiquement, le reciblage ou la publicité d’impression était difficile à prendre en compte pour les marketeurs dans l’analyse d’attribution. Les clients potentiels peuvent, à chaque fois, être exposés à des publicités de reciblage, mais il est peu probable qu’ils cliquent réellement sur l’une de ces publicités et remplissent un formulaire au cours de la même session. Notre solution d’attribution d’affichages publicitaires a désormais la possibilité de déterminer si une personne a été exposée ou non à une publicité d’impression. Ce point de contact sera ajouté à l’enregistrement individuel et sera appliqué jusqu’à ce que le prospect devienne un client. Grâce à ces informations, le spécialiste du marketing pourra désormais mieux comprendre les performances de sa publicité de reciblage.

## Qu’est-ce qui est impliqué dans la configuration de ceci ? {#what-is-involved-in-setting-this-up}

Pour [!DNL Marketo Measure] pour commencer à mesurer les impressions de publicité, une balise d’impression doit être placée dans le Gestionnaire de campagnes Doubleclick. Une fois la balise mise en oeuvre, les impressions sont stockées dans nos journaux et nous nous occupons du reste. Contactez votre gestionnaire de succès si vous souhaitez mesurer l’affichage par le biais de l’attribution.

## Quelles sont les plateformes publicitaires prises en charge ? {#which-ad-platforms-are-supported}

Nous prenons actuellement en charge Doubleclick Campaign Manager.

## Comment l’attribution est-elle calculée ? {#how-is-the-attribution-calculated}

Nous avons effectué une analyse approfondie des données d’impression et de leur influence sur les conversions à l’échelle de toutes les étapes et de tous les canaux marketing. La distribution varie en fonction du modèle, comme vous pouvez le voir dans le tableau ci-dessous :

<table> 
 <colgroup> 
  <col> 
  <col> 
  <col> 
  <col> 
  <col> 
  <col> 
  <col> 
 </colgroup> 
 <tbody> 
  <tr> 
   <th><br></th> 
   <th>Premier contact</th> 
   <th>Création de prospects</th> 
   <th>En U</th> 
   <th>En W</th> 
   <th>Chemin complet</th> 
   <th>Modèle personnalisé</th> 
  </tr> 
  <tr> 
   <td><strong>Impressions</strong></td> 
   <td>0%</td> 
   <td>0%</td> 
   <td>10 %</td> 
   <td>10 %</td> 
   <td>10 %</td> 
   <td>Personnaliser</td> 
  </tr> 
  <tr> 
   <td><strong>FT</strong></td> 
   <td>100%</td> 
   <td>0%</td> 
   <td>35 %</td> 
   <td>26.6%</td> 
   <td>20 %</td> 
   <td>Personnaliser</td> 
  </tr> 
  <tr> 
   <td><strong>LC</strong></td> 
   <td>0%</td> 
   <td>100%</td> 
   <td>35 %</td> 
   <td>26.6%</td> 
   <td>20 %</td> 
   <td>Personnaliser</td> 
  </tr> 
  <tr> 
   <td><strong>OC</strong></td> 
   <td>0%</td> 
   <td>0%</td> 
   <td>0%</td> 
   <td>26.6%</td> 
   <td>20 %</td> 
   <td>Personnaliser</td> 
  </tr> 
  <tr> 
   <td><strong>Fermées</strong></td> 
   <td>0%</td> 
   <td>0%</td> 
   <td>0%</td> 
   <td>0%</td> 
   <td>20 %</td> 
   <td>Personnaliser</td> 
  </tr> 
  <tr> 
   <td><strong>Moyen</strong></td> 
   <td>0%</td> 
   <td>0%</td> 
   <td>20 %</td> 
   <td>10 %</td> 
   <td>10 %</td> 
   <td>Personnaliser</td> 
  </tr> 
 </tbody> 
</table>

## À quoi cela ressemblera-t-il dans Salesforce ? {#what-will-this-look-like-in-salesforce}

[!DNL Marketo Measure] crée un point de contact d’impression unique sur n’importe quelle piste exposée à l’annonce publicitaire. Nous pouvons mapper l’utilisateur même une fois qu’il a consulté votre site web (FT) et qu’il a rempli un formulaire (LC). Le point de contact contiendra des informations sur la publicité, telles que le nom/l’identifiant de la campagne publicitaire, l’identifiant de la publicité, le contenu de la publicité, le nom/l’identifiant du site, le nom/l’identifiant du référent, le canal marketing, la géolocalisation, la page du référent, etc.

Le modèle d’attribution d’affichage publicitaire dépendra du client et de ses données.
