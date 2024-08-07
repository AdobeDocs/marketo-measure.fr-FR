---
unique-page-id: 37356395
description: "[!DNL Marketo Engage] Intégration de personnes - [!DNL Marketo Measure]"
title: "[!DNL Marketo Engage] Intégration de personnes"
exl-id: 51930e84-4ff8-4e35-9d44-ea017c24b051
feature: Integration
source-git-commit: 9e672d0c568ee0b889461bb8ba6fc6333edf31ce
workflow-type: tm+mt
source-wordcount: '868'
ht-degree: 2%

---

# [!DNL Marketo Engage] Intégration de personnes {#marketo-engage-people-integration}

L’intégration des personnes Marketo permet à [!DNL Marketo Measure] de commencer à télécharger des personnes à partir de Marketo et de commencer à lier leurs sessions suivies à l’individu et à mapper les points de contact à leurs engagements. Historiquement, [!DNL Marketo Measure] n’était en mesure de mapper que les points de contact à une personne du CRM. Les marketeurs peuvent ainsi mesurer leurs efforts marketing plus tôt que d’attendre une étape ou un déclencheur pour le synchroniser avec le CRM.

## Exigences {#requirements}

* Instance Marketo de production
* Instance [!DNL Salesforce] ou [!DNL Microsoft Dynamics] de production
* Tout abonnement [!DNL Marketo Measure] payant
* SOLR activé (contactez le [support Marketo](https://nation.marketo.com/t5/Support/ct-p/Support) pour activer cette fonction)

## Fonctionnement {#how-it-works}

En tant que client actuel, [!DNL Marketo Measure] télécharge déjà des personnes à partir de votre CRM. Le processus standard est que [!DNL Marketo Measure] télécharge les personnes et mappe l’adresse électronique à une session web dont nous avons effectué le suivi via bizible.js.

Avec l’introduction du téléchargement de personnes Marketo, [!DNL Marketo Measure] est désormais en mesure de mapper les sessions web à un plus grand nombre d’individus, ceux qui n’ont pas été synchronisés avec le CRM. Nous le voyons généralement en raison de processus internes qui attendent que les personnes atteignent un certain statut avant d’être transférées vers le CRM.

Lorsque [!DNL Marketo Measure] mappe avec succès la personne Marketo à une session web, notre traitement génère tous les points de contact pertinents pour celle-ci, qui sont en fin de compte reportables dans [!DNL Marketo Measure Discover]. Si cette personne Marketo est envoyée au CRM, [!DNL Marketo Measure] gérera le scénario en double et recréera le point de contact de la personne CRM, puis marquera l’ensemble initial comme &quot;doublon&quot;.

Pour que nous puissions détecter ces doublons, assurez-vous que votre synchronisation [!DNL Marketo-Salesforce] ou [!DNL Marketo-Dynamics] renseigne les ID de piste et de contact sur la personne Marketo. Si l’ID est synchronisé correctement, vous devriez être en mesure de voir l’ID de gestion de la relation client sur l’enregistrement de la personne, comme ceci :

![](assets/5a.png)

![](assets/5b.png)

Les clients ont la possibilité de créer des rapports sur l’ensemble des personnes Marketo et CRM dans [!DNL Marketo Measure] Discover. Si vous souhaitez créer des rapports uniquement sur les personnes CRM, nous vous recommandons de créer un segment afin de les filtrer.

## [!DNL Marketo Measure Discover] {#marketo-measure-discover}

Lors de la création de rapports sur les pistes (personnes) dans [!DNL Marketo Measure Discover], vous verrez le total de vos pistes Marketo et CRM. Pour créer des rapports uniquement sur les personnes Marketo ou uniquement sur les prospects CRM, vous souhaiterez créer une catégorie de segments pour votre source, puis créer des règles de segments pour Marketo et CRM à l’aide du champ &quot;Système Source&quot; pour définir la règle. Une fois vos segments créés, la catégorie Source est disponible pour les filtres sur les tableaux de bord [!DNL Marketo Measure Discover].

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
   <th><p><strong>biz_leads</strong></p></th> 
   <th><p><strong>Marketo</strong></p></th> 
  </tr> 
  <tr> 
   <td><p>ID</p></td> 
   <td><p>id</p></td> 
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
   <td><p>site web</p></td> 
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
   <td><p>Identifiant de compte (L2A)</p></td> 
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

*Il existe un problème de comportement connu où les champs de l’entité Société Marketo n’ont pas d’incidence sur la valeur updateAt de la personne. Par conséquent, si des champs pertinents tels que Site Web ou Société sont mis à jour, [!DNL Marketo Measure] ne saura pas que ces valeurs sont modifiées car la valeur date/heure de mise à jour n’est pas mise à jour. Cela a un impact sur la fonction ABM, où nous ne disposerions pas de nouvelles données pour résoudre le problème du compte de l’prospect. Il n&#39;y a pas de solution pour le moment, mais il y a des projets pour y remédier à l&#39;avenir.

## Questions fréquentes {#faq}

**Pourquoi mes nombres de pistes diffèrent-ils entre mon CRM et [!DNL Marketo Measure Discover] ?**

Comme cette intégration nous permet de créer des points de contact pour les pistes que nous avons importées directement de Marketo, il se peut que certaines pistes n’aient pas été synchronisées avec le CRM. Par conséquent, le nombre de points de contact dans Discover pourrait être supérieur à celui du CRM, puisque les points de contact ne sont transmis que pour les pistes CRM.

**Comment mes données sont-elles remplacées ?**

Cette intégration fusionne en fait les jeux de données dans votre instance [!DNL Marketo Measure] actuelle, de sorte que rien n’est remplacé. Ce que nous attendons de vos Leads CRM actuels, c’est que lorsque nous téléchargeons l’équivalent de 2 ans de Leads Marketo, nous mettions simplement à jour cet enregistrement Lead pour montrer qu’il existait également une correspondance avec un prospect Marketo. Tout cela se produit dans le serveur principal et les points de contact doivent rester identiques. Nous nous attendons également à voir plus de points de contact en raison des pistes Marketo éligibles. Si nous sommes en mesure de trouver des sessions web associées à ces personnes Marketo, nous allons commencer à voir les points de contact comptabilisés dans [!DNL Marketo Measure].

**Mes utilisateurs peuvent-ils uniquement être téléchargés à partir de Marketo et interrompre la connexion CRM ?**

Pour le moment, non. Nous aurons cette option à l’avenir, mais nous devons développer d’autres phases de cette intégration Marketo afin de pouvoir connecter les programmes, opportunités et offres de Marketo à [!DNL Marketo Measure].

**Importez-vous TOUTES mes personnes Marketo ?**

Pour l’instant, le plus tôt que nous importerons est le 1/1/2018, de sorte que nous ayons au moins 2 ans de données, ce qui est le même comportement que nous appliquons à partir des téléchargements CRM. Nous implémenterons un comportement amélioré pour télécharger une fenêtre variable de 2 ans une fois la connexion Marketo établie.

Nous ne filtrons pas non plus pour aucun type de personne, de sorte que toutes les personnes qui se trouvent dans la fenêtre de deux ans seront importées et seront éligibles pour les points de contact.

**Qu’est-ce que la SOLR et pourquoi dois-je la faire activer pour utiliser cette fonctionnalité ?**

L’activation de SOLR pour votre instance Marketo est une étape triviale qui ouvre de l’espace matériel dans Marketo afin que votre abonnement puisse utiliser l’intégration [!DNL Marketo Measure]. Si SOLR n’est pas activé, nous n’avons pas accès à certains appels qui nous permettraient sinon de télécharger les personnes appropriées à partir de votre instance Marketo.
