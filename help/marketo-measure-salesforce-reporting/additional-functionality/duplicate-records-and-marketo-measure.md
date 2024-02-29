---
unique-page-id: 18874572
description: Duplication d’enregistrements et [!DNL Marketo Measure] - [!DNL Marketo Measure]
title: Doublons d’enregistrements et  [!DNL Marketo Measure]
exl-id: e340100c-120a-4771-946d-336a1458da4e
feature: Tracking
source-git-commit: 915e9c5a968ffd9de713b4308cadb91768613fc5
workflow-type: tm+mt
source-wordcount: '288'
ht-degree: 6%

---

# Duplication d’enregistrements et [!DNL Marketo Measure] {#duplicate-records-and-marketo-measure}

>[!NOTE]
>
>Vous pouvez voir des instructions spécifiant &quot;[!DNL Marketo Measure]&quot; dans la documentation, mais consultez toujours &quot;Bizible&quot; dans votre CRM. Nous nous efforçons de mettre à jour cette version. Notre nouvelle identité (rebranding) sera bientôt répercutée dans votre CRM.

[!DNL Marketo Measure] utilise l’adresse électronique comme identifiant unique lors de la mise en correspondance des données avec un prospect ou un contact associé dans le CRM. When [!DNL Marketo Measure] trouve plusieurs Leads ou contacts avec la même adresse email, nous allons faire apparaître les mêmes données sur tous les enregistrements. L’impact de cette situation se produit lorsque vous créez des rapports sur les Leads ou les contacts avec [!DNL Marketo Measure] et peut gonfler incorrectement le nombre de personnes uniques qui ont des points de contact d’achat.

À quoi cela ressemble dans [!DNL Marketo Measure] Reporting ?

_Exemple de rapport : [!DNL Marketo Measure] Personnes avec des points de contact d’achat._

![](assets/1-1.png)

Vous pouvez voir pour la variable [!DNL Marketo Measure] ID de personne de kelsey@adobe.com indiquant qu’il existe à la fois un prospect et un contact avec cette adresse électronique. Ce rapport présente 2 Première touche, 2 Tactiles de création de piste et 2 interactions PostLC signalées. Ces enregistrements en double partagent les mêmes informations de date et de point de contact, ce qui peut conduire à la conclusion qu’ils sont deux personnes différentes, bien qu’ils soient la même personne.

**Recommandation**

* Afin d’optimiser le retour dans vos rapports, nous vous recommandons d’utiliser un outil de déduplication dans votre CRM pour vous assurer que vous ne créez que des enregistrements nets nouveaux et uniques. Vous pouvez le faire avec votre outil d’automatisation du marketing ou avec un logiciel distinct installé dans votre CRM. [!DNL Marketo Measure] ne déduplique pas automatiquement les enregistrements et ne propose pas ce service par le biais de notre logiciel.
* Une autre option consiste à fusionner manuellement les enregistrements lorsque vous identifiez des doublons. Ce processus peut être fastidieux et chronophage, mais la production de rapports précis vaut la peine d’être investie dans le temps.
