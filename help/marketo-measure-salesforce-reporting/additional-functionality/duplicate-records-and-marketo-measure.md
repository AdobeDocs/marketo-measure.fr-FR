---
description: Dupliquer les enregistrements et [!DNL Marketo Measure] - [!DNL Marketo Measure]
title: Doublons d’enregistrements et  [!DNL Marketo Measure]
exl-id: e340100c-120a-4771-946d-336a1458da4e
feature: Tracking
source-git-commit: c6090ce0c3ac60cd68b1057c369ce0b3b20aeeee
workflow-type: tm+mt
source-wordcount: '279'
ht-degree: 12%

---


# Dupliquer les enregistrements et les [!DNL Marketo Measure] {#duplicate-records-and-marketo-measure}

>[!NOTE]
>Des instructions spécifiant « [!DNL Marketo Measure] » peuvent s’afficher dans la documentation. Toutefois, votre gestion de la relation client (CRM) mentionne encore « Bizible ». Nous nous efforçons de mettre cela à jour. Notre nouvelle identité de marque (rebranding) sera bientôt répercutée dans votre CRM.

[!DNL Marketo Measure] utilise l’adresse e-mail comme identifiant unique lors de la mise en correspondance de données avec un lead ou un contact associé dans le CRM. Lorsque [!DNL Marketo Measure] trouve plusieurs prospects ou contacts avec la même adresse e-mail, nous affichons les mêmes données sur tous les enregistrements. L’impact de cette situation se produit lorsque vous établissez des rapports sur les leads ou les contacts avec [!DNL Marketo Measure] et que vous pouvez gonfler à tort le nombre de personnes uniques qui disposent de points de contact d’acheteur.

À quoi cela ressemble-t-il dans [!DNL Marketo Measure] Reporting ?

_Exemple de rapport : [!DNL Marketo Measure] de personnes avec des points de contact d’acheteur._

![&#x200B; 1](assets/1-1.png)

Vous pouvez voir pour l’ID de personne [!DNL Marketo Measure] de kelsey@adobe.com qu’il existe à la fois un prospect et un contact avec cette adresse e-mail. Dans ce rapport, deux premiers contacts ont été signalés, deux contacts de création de leads et deux interactions PostLC ont été signalées. Ces enregistrements en double partagent des informations de date et de point de contact qui pourraient conduire à la conclusion qu’il s’agit de deux personnes différentes bien qu’elles soient la même personne.

**Recommandation**

* Pour optimiser le retour sur investissement de vos rapports , nous vous recommandons d’utiliser un outil de déduplication dans votre CRM afin de vous assurer que vous ne créez que de nouveaux enregistrements uniques. Pour ce faire, utilisez votre outil d’automatisation du marketing ou un logiciel distinct installé dans votre CRM. [!DNL Marketo Measure] ne déduplique pas automatiquement les enregistrements et n&#39;offre pas ce service via notre logiciel.
* Une autre option consiste à fusionner manuellement les enregistrements au fur et à mesure que vous identifiez les doublons. Ce processus peut être long et fastidieux, mais le résultat d’un compte rendu des performances précis vaut la peine d’être investi en temps.
