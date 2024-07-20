---
unique-page-id: 18874592
description: Intégration du suivi des appels - [!DNL Marketo Measure]
title: Intégration du suivi d’appel
exl-id: bc35a789-e056-4456-9038-306ed34c2a8e
feature: Tracking, Integration
source-git-commit: 4787f765348da71bc149c997470ce678ba498772
workflow-type: tm+mt
source-wordcount: '693'
ht-degree: 1%

---

# Intégration du suivi d’appel {#call-tracking-integration}

Notre intégration à [!DNL CallTrackingMetrics] est destinée à fusionner une session web avec un appel téléphonique. Un appel téléphonique est traité comme un envoi de formulaire à [!DNL Marketo Measure]. Il accorde du crédit à une session web qui, autrement, n’aurait été considérée qu’une visite web car il n’y avait pas eu d’envoi réel de formulaire.

## Explication du suivi des appels {#call-tracking-explained}

&quot;Suivi des appels&quot; au sens général est un produit de sociétés telles que [!DNL CallTrackingMetrics], [!DNL DiaglogTech], [!DNL Invoca] ou [!DNL CallRail], pour n’en nommer que quelques-unes. Les numéros de téléphone uniques sont affichés aux utilisateurs en fonction des différents canaux marketing ou campagnes d’où ils proviennent. Cela permet aux spécialistes du marketing de déterminer les performances de ces canaux ou campagnes.

![](assets/1.png)

## Avant et après {#before-and-after}

Consultez l’organigramme ci-dessous pour voir comment [!DNL Marketo Measure] a utilisé pour gérer les appels téléphoniques sans intégration à CallTrackingMetrics. L’appel téléphonique qui a eu lieu n’a pas fait l’objet d’un suivi, il a donc été considéré comme une session web et aucun point de contact n’a été créé pour celui-ci. Ce n’est qu’au cours de la prochaine visite que l’utilisateur a rempli un formulaire qu’un point de contact a finalement été renseigné.

Avec l’intégration, vous pouvez voir que la session web a été liée à un appel téléphonique. Le prochain remplissage de formulaire se présente sous la forme d’une touche PostLC et est toujours suivi dans le cadre du parcours.

![](assets/2.png)

## Fonctionnement {#how-it-works}

CallTrackingMetrics doit effectuer un certain travail de développement pour que cela fonctionne. Avec le JavaScript qu’il place sur votre site, CallTrackingMetrics peut prendre _biz_uid du cookie [!DNL Marketo Measure]. Ce &quot;[!DNL BizibleId]&quot; est ensuite stocké par CallTrackingMetrics.

Lorsqu’un visiteur se rend sur votre site et effectue un appel téléphonique, la tâche de CallTrackingMetrics est de transmettre ces données dans [!DNL Salesforce].  En règle générale, un [!DNL Salesforce Task] est créé pour renseigner des données telles que le numéro de téléphone, l’objet, le type et maintenant, le [!DNL BizibleId]

[!DNL BizibleId] est un champ installé avec la version 6.7+ du package d’attribution marketing [!DNL Marketo Measure].

Vous trouverez ci-dessous un exemple d’enregistrement de tâche avec le [!DNL BizibleId] renseigné.

![](assets/3.png)

Lorsque [!DNL Marketo Measure] trouve un enregistrement de tâche avec une valeur [!DNL BizibleId] connue renseignée, [!DNL Marketo Measure] peut mapper cet utilisateur à une session web avec le même [!DNL BizibleId] et attribuer cette session à un appel téléphonique au lieu d’une visite web.

## Point de contact {#the-touchpoint}

Lorsque [!DNL Marketo Measure] peut importer/télécharger la tâche, nous traitons ce détail avec la session web. En règle générale, il peut être fusionné avec un référent ou une publicité. Dans l’exemple ci-dessous, un visiteur a trouvé l’entreprise via une publicité Google payante et a effectué un appel téléphonique.

Le type [!UICONTROL Point de contact] &quot;Appel&quot; est extrait de la tâche, de la capture d’écran ci-dessus, qui est également renseignée par CallTrackingMetrics lors de la création de la tâche.

![](assets/4.png)

## Création de rapports {#reporting}

Les valeurs Type de point de contact que [!DNL Marketo Measure] envoie généralement sont Visite Web, Formulaire Web ou Conversation Web, mais dans le cas des points de contact CallTrackingMetrics, le type de point de contact est Appel téléphonique. Les marketeurs peuvent ainsi identifier les canaux qui attirent le plus d’appels téléphoniques et qui génèrent des recettes pour leur entreprise.

![](assets/5.png)

## Questions fréquentes {#faq}

**Pourquoi ma visite web de type point de contact ?**

Le type de point de contact est renseigné à partir du champ Task.Type . Si le champ Task.Type est vide, [!DNL Marketo Measure] définit automatiquement le type de point de contact comme visite web. Une fois que le champ Task.Type est renseigné [!DNL Marketo Measure], cette valeur est lue et le type de point de contact est renseigné en conséquence.

**Quels autres champs le point de contact renseigne-t-il à partir de l’appel téléphonique ?**

Le type de point de contact et Medium contiennent tous deux les données extraites de Task.Type. Tous les autres points de données sont extraits du suivi web et des données JavaScript.

**Pourquoi cet appel téléphonique n’est-il pas lié à une session web ?**

Tout d’abord, vérifiez la tâche pour vous assurer qu’un [!DNL BizibleId] est renseigné. S’il n’y a aucune valeur, nous ne pouvons pas créer de point de contact pour celui-ci. Cela doit être réaffecté avec CallTrackingMetrics.

S’il existe une valeur, notez que toutes les sessions web ne sont prises en compte que pour 30 minutes. Si un utilisateur a cliqué sur une publicité Google à 12h17 (début de la session sur le site web), mais que l’appel téléphonique n’a pas eu lieu avant 13h05, nous ne fusionnerons pas la session web et l’appel téléphonique. Au contraire, [!DNL Marketo Measure] crée un point de contact [!DNL Salesforce Task] distinct pour effectuer le suivi de l’appel téléphonique, mais ne disposera d’aucune donnée de session Web.

![](assets/6.png)

## Partenariats {#partnerships}

[!DNL Marketo Measure] a actuellement un partenaire officiel de suivi des appels qui a passé avec nous le processus d’intégration &quot;officiel&quot;, qui inclut le co-marketing et la formation aux produits. Ce partenaire unique est CallTrackingMetrics.
