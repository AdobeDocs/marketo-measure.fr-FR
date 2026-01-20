---
unique-page-id: 18874652
description: FAQ sur l’attribution de [!DNL Marketo Measure] View Through - [!DNL Marketo Measure]
title: Questions fréquentes sur l’attribution de visionnage moyen dans [!DNL Marketo Measure]
exl-id: d20e88f3-3ff8-4381-a4b8-6862798caa74
feature: Attribution
source-git-commit: 666812e8bf095170d611cd694b5d0ac5151d8fdd
workflow-type: tm+mt
source-wordcount: '492'
ht-degree: 31%

---

# Questions fréquentes sur l’attribution de visionnage moyen dans [!DNL Marketo Measure] {#marketo-measure-view-through-attribution-faq}

## Qu’est-ce que l’attribution Afficher via ? {#what-is-view-through-attribution}

La fonction [!DNL Marketo Measure] [!UICONTROL Afficher via l’attribution] permet d’inclure des impressions d’annonce publicitaire dans le modèle d’attribution.

>[!IMPORTANT]
>
>En raison de problèmes de confidentialité, des cookies tiers sont en cours d’élimination. L’abandon des cookies tiers annoncé par Google Chrome au troisième trimestre 2024 marque effectivement la fin de cette forme de suivi. Par conséquent, Adobe abandonnera les fonctions Marketo Measure qui reposent sur des cookies tiers, en particulier le suivi inter-domaines et l’attribution après affichage (View-through), qui utilisent le cookie d’impression Google/DoubleClick. Aucune autre fonction de Marketo Measure ne sera affectée. L’utilisation des cookies propriétaires ne sera pas non plus affectée. Compte tenu du planning de Google, la date d’obsolescence attendue des deux fonctions ci-dessus est le 01/06/2024. Les données connexes collectées avant cette date restent disponibles pour les clientes et clients Adobe.

## Pourquoi la fonction [!UICONTROL Afficher via l’attribution] est-elle importante ? {#why-is-view-through-attribution-important}

Historiquement, le reciblage ou la publicité d’impression ont été difficiles à prendre en compte par les spécialistes marketing dans l’analyse d’attribution. Les clients potentiels peuvent être exposés à maintes reprises à des publicités de reciblage, mais il est peu probable qu’ils cliquent sur l’une de ces publicités et remplissent un formulaire au cours de la même session. Notre solution Afficher via l’attribution peut désormais déterminer si une personne a été exposée à une publicité sous forme d’impression. Ce point de contact sera ajouté à l’enregistrement individuel et se poursuivra jusqu’à ce que le prospect devienne un client. Grâce à ces informations, le marketeur peut désormais obtenir de meilleurs résultats pour insight en ce qui concerne sa publicité de reciblage.

## Qu’est-ce que cela implique ? {#what-is-involved-in-setting-this-up}

Pour que [!DNL Marketo Measure] puissiez commencer à mesurer les impressions d’annonces, une balise d’impression doit être placée dans Doubleclick Campaign Manager. Une fois la balise implémentée, les impressions sont stockées dans nos journaux et nous nous occupons du reste. Contactez votre responsable du succès client si vous souhaitez mesurer la vue par le biais de l’attribution.

## Quelles sont les plateformes publicitaires prises en charge ? {#which-ad-platforms-are-supported}

Nous prenons actuellement en charge [!DNL Doubleclick] Campaign Manager.

## Comment l’attribution est-elle calculée ? {#how-is-the-attribution-calculated}

Nous avons effectué une analyse approfondie des données d’impression et de leur influence sur les conversions à toutes les étapes et sur les canaux marketing. La distribution varie en fonction du modèle, comme vous pouvez le voir dans le tableau ci-dessous :

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
   <th>En forme de U</th> 
   <th>En W</th> 
   <th>Chemin complet</th> 
   <th>Modèle personnalisé</th> 
  </tr> 
  <tr> 
   <td><strong>Impressions</strong></td> 
   <td>0 %</td> 
   <td>0 %</td> 
   <td>10 %</td> 
   <td>10 %</td> 
   <td>10 %</td> 
   <td>Personnalisé</td> 
  </tr> 
  <tr> 
   <td><strong>FT</strong></td> 
   <td>100 %</td> 
   <td>0 %</td> 
   <td>35 %</td> 
   <td>26,6 %</td> 
   <td>20 %</td> 
   <td>Personnalisé</td> 
  </tr> 
  <tr> 
   <td><strong>LC</strong></td> 
   <td>0 %</td> 
   <td>100 %</td> 
   <td>35 %</td> 
   <td>26,6 %</td> 
   <td>20 %</td> 
   <td>Personnalisé</td> 
  </tr> 
  <tr> 
   <td><strong>OC</strong></td> 
   <td>0 %</td> 
   <td>0 %</td> 
   <td>0 %</td> 
   <td>26,6 %</td> 
   <td>20 %</td> 
   <td>Personnalisé</td> 
  </tr> 
  <tr> 
   <td><strong>Fermées</strong></td> 
   <td>0 %</td> 
   <td>0 %</td> 
   <td>0 %</td> 
   <td>0 %</td> 
   <td>20 %</td> 
   <td>Personnalisé</td> 
  </tr> 
  <tr> 
   <td><strong>Deuxième prénom</strong></td> 
   <td>0 %</td> 
   <td>0 %</td> 
   <td>20 %</td> 
   <td>10 %</td> 
   <td>10 %</td> 
   <td>Personnalisé</td> 
  </tr> 
 </tbody> 
</table>

## À quoi cela ressemblera-t-il dans [!DNL Salesforce?] {#what-will-this-look-like-in-salesforce}

[!DNL Marketo Measure] créera un point de contact d’impression unique sur tout prospect exposé à l’annonce publicitaire. Nous sommes en mesure de mapper l&#39;utilisateur même après sa première visite sur votre site Web (FT) et de remplir un formulaire (LC). Le point de contact contiendra des informations publicitaires telles que le nom/l’identifiant de la campagne publicitaire, l’identifiant de la publicité, le contenu de la publicité, le nom/l’identifiant du site, le nom/l’identifiant de l’emplacement, le canal marketing, la zone géographique, la page du référent, etc.

Le modèle d’attribution d’affichage publicitaire dépend du client et de ses données.
