---
unique-page-id: 18874592
description: Intégration du suivi des appels - [!DNL Marketo Measure] - Documentation du produit
title: Intégration du suivi d’appel
exl-id: bc35a789-e056-4456-9038-306ed34c2a8e
source-git-commit: 09ffdbb0b1baeed870a3145268997e63a3707c97
workflow-type: tm+mt
source-wordcount: '708'
ht-degree: 0%

---

# Intégration du suivi d’appel {#call-tracking-integration}

Notre intégration avec [!DNL CallTrackingMetrics] est conçu pour fusionner une session web avec un appel téléphonique. Un appel téléphonique est traité comme un envoi de formulaire à [!DNL Marketo Measure]. Il accorde du crédit à une session web qui, autrement, n’aurait été considérée qu’une visite web car il n’y avait pas eu d’envoi réel de formulaire.

## Explication du suivi des appels {#call-tracking-explained}

&quot;Suivi des appels&quot; au sens général est un produit provenant de sociétés telles que [!DNL CallTrackingMetrics], [!DNL DiaglogTech], [!DNL Invoca]ou [!DNL CallRail], pour n’en citer que quelques-uns. Les numéros de téléphone uniques sont affichés aux utilisateurs en fonction des différents canaux marketing ou campagnes d’où ils proviennent. Cela permet aux spécialistes du marketing de déterminer les performances de ces canaux ou campagnes.

![](assets/1.png)

## Avant et après {#before-and-after}

Consultez l’organigramme ci-dessous pour découvrir comment [!DNL Marketo Measure] utilisé pour gérer les appels téléphoniques sans intégration à CallTrackingMetrics. L’appel téléphonique qui a eu lieu n’a pas fait l’objet d’un suivi, il a donc été considéré comme une session web et aucun point de contact n’a été créé pour celui-ci. Ce n’est qu’au cours de la prochaine visite que l’utilisateur a rempli un formulaire qu’un point de contact a finalement été renseigné.

Avec l’intégration, vous pouvez voir que la session web a été liée à un appel téléphonique. Le prochain remplissage de formulaire se présente sous la forme d’une touche PostLC et est toujours suivi dans le cadre du parcours.

![](assets/2.png)

## Fonctionnement {#how-it-works}

CallTrackingMetrics doit faire un peu de travail de développement de son côté pour que cela fonctionne. Avec le code JavaScript qu’il place sur votre site, CallTrackingMetrics peut récupérer le _biz_uid de la variable [!DNL Marketo Measure] du cookie. Ce &quot;[!DNL BizibleId]&quot; est ensuite stocké par CallTrackingMetrics.

Lorsqu’un visiteur se rend sur votre site et effectue un appel téléphonique, la fonction CallTrackingMetrics de transmettre ces données à [!DNL Salesforce]  En règle générale, une [!DNL Salesforce Task] est créé pour renseigner des données telles que le numéro de téléphone, l’objet, le type, et maintenant, la variable [!DNL BizibleId]

Le [!DNL BizibleId] est un champ installé avec la version 6.7+ de la variable [!DNL Marketo Measure] Package d’attribution marketing.

Vous trouverez ci-dessous un exemple d’enregistrement de tâche avec la fonction [!DNL BizibleId] renseignée.

![](assets/3.png)

When [!DNL Marketo Measure] Trouve un enregistrement de tâche avec un connu [!DNL BizibleId] valeur renseignée, [!DNL Marketo Measure] peut mapper cet utilisateur à une session web avec le même [!DNL BizibleId] et attribuez cette session à un appel téléphonique au lieu d’une visite web.

## Point de contact {#the-touchpoint}

When [!DNL Marketo Measure] peut importer/télécharger la tâche, nous traitons ce détail avec la session web. Dans la plupart des cas, il peut être fusionné avec un référent ou une publicité. Dans l’exemple ci-dessous, un visiteur a trouvé l’entreprise par le biais d’une publicité Google payante et a effectué un appel téléphonique.

Le [!UICONTROL Point de contact] Le type &quot;Appel&quot; est extrait de la tâche, de la capture d’écran ci-dessus, qui est également renseignée par CallTrackingMetrics lors de la création de la tâche.

![](assets/4.png)

## Production de rapports {#reporting}

Valeurs de type de point de contact qui [!DNL Marketo Measure] Les notifications push sont généralement des visites web, des formulaires web ou des conversations web, mais dans le cas des points de contact CallTrackingMetrics, le type de point de contact est Appel téléphonique. Les marketeurs peuvent ainsi identifier les canaux qui attirent le plus d’appels téléphoniques et qui génèrent des recettes pour leur entreprise.

![](assets/5.png)

## FAQ {#faq}

**Pourquoi ma visite web de type point de contact ?**

Le type de point de contact est renseigné à partir du champ Task.Type . Si le champ Task.Type est vide, alors [!DNL Marketo Measure] définit automatiquement le type de point de contact sur Visite web. Une fois le champ Task.Type renseigné [!DNL Marketo Measure] liront cette valeur et renseigneront le type de point de contact en conséquence.

**Quels autres champs le point de contact renseigne-t-il à partir de l’appel téléphonique ?**

Le type de point de contact et le support contiennent tous deux les données extraites de Task.Type. Tous les autres points de données sont extraits du suivi web et des données JavaScript.

**Pourquoi cet appel téléphonique n’est-il pas lié à une session web ?**

Tout d’abord, vérifiez la tâche pour vous assurer qu’une [!DNL BizibleId] renseignée. S’il n’y a aucune valeur, nous ne créerons pas et ne pourrons pas créer de point de contact pour celui-ci. Cela doit être réaffecté avec CallTrackingMetrics.

S’il existe une valeur, notez que toutes les sessions web ne sont prises en compte que pour 30 minutes. Si un utilisateur a cliqué sur une publicité Google à 12h17 (début de la session sur le site web), mais que l’appel téléphonique n’a pas eu lieu avant 13h05, nous ne fusionnerons pas la session web et l’appel téléphonique. En revanche, [!DNL Marketo Measure] crée un [!DNL Salesforce Task] point de contact pour effectuer le suivi de l’appel téléphonique, mais ne contiendra aucune donnée de session web.

![](assets/6.png)

## Partenariats {#partnerships}

[!DNL Marketo Measure] dispose actuellement d’un partenaire officiel de suivi des appels qui a passé avec nous le processus &quot;officiel&quot; d’intégration, qui inclut le co-marketing et la formation aux produits. Ce partenaire unique est CallTrackingMetrics.
