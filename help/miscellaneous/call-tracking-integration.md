---
description: Intégration du suivi d’appel - [!DNL Marketo Measure]
title: Intégration du suivi d’appel
exl-id: bc35a789-e056-4456-9038-306ed34c2a8e
feature: Tracking, Integration
source-git-commit: c6090ce0c3ac60cd68b1057c369ce0b3b20aeeee
workflow-type: tm+mt
source-wordcount: '767'
ht-degree: 1%

---


# Intégration du suivi d’appel {#call-tracking-integration}

Notre intégration à [!DNL CallTrackingMetrics] est destinée à fusionner une session web avec un appel téléphonique. Un appel téléphonique est traité comme un envoi de formulaire à [!DNL Marketo Measure]. Il fait référence à une session web qui n’aurait autrement été considérée que comme une visite web, car il n’y avait pas eu d’envoi de formulaire réel.

## Présentation du suivi d’appels {#call-tracking-explained}

Le « suivi d’appels » au sens général est un produit de sociétés telles que [!DNL CallTrackingMetrics], [!DNL DiaglogTech], [!DNL Invoca] ou [!DNL CallRail], pour n’en citer que quelques-unes. Les numéros de téléphone uniques sont affichés aux utilisateurs en fonction des différents canaux ou campagnes marketing d’où ils proviennent. Cela permet aux spécialistes du marketing de voir les performances de ces canaux ou campagnes.

![Diagramme affichant des numéros de téléphone uniques en fonction de différents canaux et campagnes marketing](assets/1.png)

## Avant et Après {#before-and-after}

Examinez le diagramme de flux ci-dessous pour voir comment [!DNL Marketo Measure] utilisait pour gérer les appels téléphoniques sans intégration à CallTrackingMetrics. L’appel téléphonique qui a eu lieu n’a pas été suivi, il a donc été considéré comme une session web et aucun point de contact n’a été créé pour celle-ci. Ce n’est qu’à la prochaine visite au cours de laquelle l’utilisateur a rempli un formulaire qu’un point de contact a finalement été renseigné.

Avec l’intégration, vous pouvez voir que la session web a été liée à un appel téléphonique. Le remplissage du formulaire suivant finit par être un contact PostLC et est toujours suivi dans le cadre du parcours.

![Organigramme comparant le suivi des appels téléphoniques avant et après l’intégration de CallTrackingMetrics](assets/2.png)

## Fonctionnement {#how-it-works}

CallTrackingMetrics doit effectuer des tâches de développement de son côté pour que cela fonctionne. Avec le JavaScript qu’ils placent sur votre site, CallTrackingMetrics peut récupérer _biz_uid à partir du cookie [!DNL Marketo Measure]. Ce « [!DNL BizibleId] » est ensuite stocké par CallTrackingMetrics.

Lorsqu’un visiteur se rend sur votre site et passe un appel téléphonique, la tâche de CallTrackingMetrics consiste à transmettre ces données à [!DNL Salesforce].  En règle générale, une [!DNL Salesforce Task] est créée pour renseigner des données telles que le numéro de téléphone, l’objet, le type et, désormais, le [!DNL BizibleId]

Le [!DNL BizibleId] est un champ qui est installé avec la version 6.7 ou ultérieure du package d’attribution marketing [!DNL Marketo Measure].

Vous trouverez ci-dessous un exemple d’enregistrement de tâche avec le [!DNL BizibleId] renseigné.

![Exemple d’enregistrement de tâche Salesforce affichant le champ BizibleId renseigné avec la valeur ](assets/3.png)

Lorsque [!DNL Marketo Measure] trouve un enregistrement de tâche avec une valeur de [!DNL BizibleId] connue renseigné, [!DNL Marketo Measure] pouvez mapper cet utilisateur à une session web avec le même [!DNL BizibleId] et attribuer cette session à un appel téléphonique plutôt qu’à une visite web.

## Le point de contact {#the-touchpoint}

Lorsque [!DNL Marketo Measure] pouvons importer ou télécharger la tâche, nous traitons ce détail avec la session web. En règle générale, il peut être fusionné avec un référent ou une annonce publicitaire. Dans l’exemple ci-dessous, un visiteur a trouvé l’entreprise par le biais d’une annonce Google payante et a passé un appel téléphonique.

Le type [!UICONTROL Appel de point de contact] est extrait de la tâche, à partir de la capture d’écran ci-dessus, qui est également renseignée par CallTrackingMetrics lorsque la tâche est créée.

![Enregistrement de point de contact affichant le type comme appel à partir des données de session web et d’appel téléphonique fusionnées](assets/4.png)

## Rapports {#reporting}

Les valeurs de type de point de contact que [!DNL Marketo Measure] envoie généralement sont Visite web, Formulaire web ou Conversation web, mais dans le cas des points de contact CallTrackingMetrics, le type de point de contact est Appel téléphonique. Cela permet aux professionnels du marketing de voir quels canaux attirent le plus d’appels téléphoniques et génèrent des revenus pour leur organisation.

![Rapport affichant les types de points de contact, y compris les appels téléphoniques pour le suivi du chiffre d’affaires généré par les appels par canal](assets/5.png)

## Questions fréquentes {#faq}

**Pourquoi ma visite web de type point de contact ?**

Le type de point de contact est renseigné à partir du champ Task.Type. Si le champ Task.Type est vide, [!DNL Marketo Measure] définit automatiquement le type de point de contact sur Visite web. Une fois le champ Task.Type renseigné, [!DNL Marketo Measure] lirez cette valeur et renseignez le type de point de contact en conséquence.

**Quels autres champs le point de contact remplit-il à partir de l’appel téléphonique ?**

Le type de point de contact et Medium contiennent tous deux les données extraites du fichier Task.Type. Tous les autres points de données sont extraits des données JavaScript et de suivi web.

**Pourquoi cet appel téléphonique n’est-il pas lié à une session web ?**

Tout d’abord, vérifiez qu’une [!DNL BizibleId] est renseignée dans la tâche. S’il n’existe aucune valeur, nous ne pouvons pas créer de point de contact pour celui-ci. Cette erreur doit être signalée avec CallTrackingMetrics.

S’il existe une valeur, notez que nous ne considérons que les sessions web de 30 minutes. Si vous avez cliqué sur une publicité Google à 12 :17pm (début de la session sur le site web), mais que l’appel téléphonique n’a pas eu lieu avant le 1:05pm, nous ne fusionnerons pas la session web et l’appel téléphonique. À la place, [!DNL Marketo Measure] crée un point de contact [!DNL Salesforce Task] distinct pour suivre l’appel téléphonique, mais ne dispose d’aucune donnée de session web.

![Diagramme affichant le délai d’expiration de 30 minutes d’une session web entre un clic publicitaire et un appel téléphonique](assets/6.png)

## Partenariats {#partnerships}

[!DNL Marketo Measure] a actuellement un partenaire de suivi des appels officiel qui a suivi le processus d’intégration « officiel » avec nous, qui incluait le co-marketing et la formation sur les produits. Ce partenaire est CallTrackingMetrics.
