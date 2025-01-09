---
unique-page-id: 37356395
description: Intégration des personnes [!DNL Marketo Engage] - [!DNL Marketo Measure]
title: Intégration des personnes [!DNL Marketo Engage]
exl-id: 51930e84-4ff8-4e35-9d44-ea017c24b051
feature: Integration
source-git-commit: de366de2d1df3d4dc9fc33e5fd0dab225b6af081
workflow-type: tm+mt
source-wordcount: '868'
ht-degree: 2%

---

# Intégration des personnes [!DNL Marketo Engage] {#marketo-engage-people-integration}

L’intégration des personnes de Marketo [!DNL Marketo Measure] permet de commencer à télécharger des personnes à partir de Marketo et de lier leurs sessions suivies à l’individu et de mapper les points de contact à leurs engagements. Historiquement, [!DNL Marketo Measure] ne pouvait mapper les points de contact qu’à une personne à partir du CRM, ce qui permet aux spécialistes marketing de mesurer leurs efforts marketing plus rapidement plutôt que d’attendre une étape ou un déclencheur pour les synchroniser avec le CRM.

## Exigences {#requirements}

* Instance de Marketo de production
* [!DNL Salesforce] de production ou instance de [!DNL Microsoft Dynamics]
* Tout abonnement [!DNL Marketo Measure] payant
* SOLR activé (contactez l’assistance technique de [Marketo](https://nation.marketo.com/t5/Support/ct-p/Support){target="_blank"} pour que cela soit activé)

## Fonctionnement {#how-it-works}

En tant que client actuel, [!DNL Marketo Measure] télécharge déjà des personnes à partir de votre CRM. Le processus standard consiste à télécharger [!DNL Marketo Measure] les personnes et à mapper l’adresse e-mail à une session web que nous avons suivie via Bizible.js.

Avec l’introduction du téléchargement des utilisateurs de Marketo, [!DNL Marketo Measure] est désormais en mesure de mapper les sessions web à un plus grand groupe d’utilisateurs, ceux qui n’ont pas été synchronisés avec le CRM. Cela est généralement dû à des processus internes qui attendent que les personnes atteignent un certain statut avant d’être transmises au CRM.

Lorsque [!DNL Marketo Measure] parvenez à mapper la personne Marketo à une session web, notre traitement génère tous les points de contact pertinents pour celle-ci, qui doivent en fin de compte être signalés dans [!DNL Marketo Measure Discover]. Si cette personne Marketo est envoyée au CRM, [!DNL Marketo Measure] gérerons le scénario en double, nous recréerons le point de contact pour la personne CRM et marquerons le jeu initial comme « en double ».

Pour que nous puissions détecter ces doublons, assurez-vous que votre [!DNL Marketo-Salesforce] ou [!DNL Marketo-Dynamics] synchronisation renseigne les ID de lead et de contact sur la personne Marketo. Si l’ID se synchronise correctement, vous devriez être en mesure de voir l’ID CRM sur l’enregistrement de personne, comme suit :

![](assets/5a.png)

![](assets/5b.png)

Les clients ont la possibilité de signaler l’ensemble des personnes Marketo et des personnes CRM dans [!DNL Marketo Measure] Discover. Si vous souhaitez créer des rapports uniquement pour les personnes qui utilisent CRM, nous vous recommandons de créer un segment pour les filtrer.

## [!DNL Marketo Measure Discover] {#marketo-measure-discover}

Lors de la création de rapports sur les prospects (personnes) dans [!DNL Marketo Measure Discover], vous verrez le total de vos prospects Marketo et CRM. Pour générer des rapports portant uniquement sur des personnes Marketo ou uniquement sur des prospects CRM, vous devez créer une catégorie de segments pour votre source, puis créer des règles de segments pour Marketo et CRM à l’aide du champ « Système Source » pour définir la règle. Une fois vos segments créés, la catégorie Source est disponible pour être filtrée dans vos tableaux de bord [!DNL Marketo Measure Discover].

![](assets/bizible-discover-1.png)

![](assets/bizible-discover-2.png)

## Appariement des champs {#field-mappings}

<table> 
 <colgroup> 
  <col> 
  <col> 
 </colgroup> 
 <tbody> 
  <tr> 
   <th><p><strong>leads de l’entreprise</strong></p></th> 
   <th><p><strong>Marketo</strong></p></th> 
  </tr> 
  <tr> 
   <td><p>ID</p></td> 
   <td><p>identifiant</p></td> 
  </tr> 
  <tr> 
   <td><p>MODIFIED_DATE</p></td> 
   <td><p>updatedAt<strong>*</strong></p></td> 
  </tr> 
  <tr> 
   <td><p>CREATED_DATE</p></td> 
   <td><p>createdAt</p></td> 
  </tr> 
  <tr> 
   <td><p>EMAIL</p></td> 
   <td><p>E-mail</p></td> 
  </tr> 
  <tr> 
   <td><p>WEB_SITE</p></td> 
   <td><p>site internet</p></td> 
  </tr> 
  <tr> 
   <td><p>COMPANY</p></td> 
   <td><p>société</p></td> 
  </tr> 
  <tr> 
   <td><p>IS_CONVERTED</p></td> 
   <td><p>s/o</p></td> 
  </tr> 
  <tr> 
   <td><p>ACCOUNT_ID</p></td> 
   <td><p>Id De Compte (L2A)</p></td> 
  </tr> 
  <tr> 
   <td><p>BIZIBLE_STAGE</p></td> 
   <td><p>Statut</p></td> 
  </tr> 
  <tr> 
   <td><p>IS_DELETED</p></td> 
   <td><p>true/false</p></td> 
  </tr> 
 </tbody> 
</table>

*Il existe un problème de comportement connu où les champs de l’entité Société Marketo n’ont aucune incidence sur la valeur updatedAt de la personne. Par conséquent, si des champs pertinents tels que Site web ou Société sont mis à jour, [!DNL Marketo Measure] ne saura pas que ces valeurs sont modifiées, car la valeur date/heure updatedAt n’est pas mise à jour. Cela a un impact sur la fonctionnalité ABM, car nous n’aurions pas de données récentes pour résoudre le compte pour le prospect. Il n&#39;y a pas de solution de contournement pour le moment, mais il est prévu d&#39;y remédier à l&#39;avenir.

## Questions fréquentes {#faq}

**Pourquoi mon nombre de leads diffère-t-il entre mon CRM et [!DNL Marketo Measure Discover] ?**

Comme cette intégration nous permet de créer des points de contact pour les prospects que nous avons importés directement de Marketo, il se peut que certains prospects n’aient pas été synchronisés avec le CRM, par conséquent le nombre dans Discover peut être supérieur à celui du CRM, puisque les points de contact ne sont transmis que pour les prospects du CRM.

**Comment cela remplace-t-il mes données ?**

Cette intégration fusionne en fait les jeux de données au sein de votre instance [!DNL Marketo Measure] actuelle afin que rien ne soit remplacé. Ce que nous attendons de vos prospects CRM actuels, c’est que lorsque nous téléchargeons l’équivalent de 2 ans de prospects Marketo, nous mettions simplement à jour cet enregistrement de prospect afin d’indiquer qu’il existe également une correspondance avec un prospect Marketo. Tout se passe en arrière-plan et les points de contact devraient rester les mêmes. Nous nous attendons également à voir plus de points de contact en raison des prospects Marketo éligibles. Si nous parvenons à trouver des sessions web correspondant à ces personnes de Marketo, nous commencerons à voir les points de contact comptabilisés dans [!DNL Marketo Measure].

**Puis-je uniquement télécharger mes salariés depuis Marketo et couper la connexion CRM ?**

Pour l&#39;instant, non. Nous aurons cette option à l’avenir, mais nous devons développer d’autres phases de cette intégration de Marketo afin de pouvoir connecter les programmes, les opportunités et les offres de Marketo à [!DNL Marketo Measure].

**Importez-vous TOUS mes collaborateurs Marketo ?**

Pour le moment, nous allons importer les données au plus tôt à partir du 1/1/2018 afin de disposer d’un minimum de 2 ans de données, ce qui est le même comportement que nous appliquons à partir des téléchargements CRM. Nous implémenterons un comportement amélioré pour télécharger une fenêtre dynamique de 2 ans une fois la connexion Marketo établie.

Nous ne filtrons pas non plus les types de personnes, de sorte que toutes les personnes dans la fenêtre de deux ans seront importées et sont éligibles aux points de contact.

**Qu’est-ce que SOLR et pourquoi dois-je l’activer pour utiliser cette fonctionnalité ?**

L’activation de SOLR pour votre instance Marketo est une étape triviale qui ouvre de l’espace matériel dans Marketo afin que votre abonnement puisse utiliser l’intégration [!DNL Marketo Measure]. Si SOLR n’est pas activé, nous n’avons pas accès à certains appels qui nous permettraient autrement de télécharger les personnes appropriées à partir de votre instance Marketo.
