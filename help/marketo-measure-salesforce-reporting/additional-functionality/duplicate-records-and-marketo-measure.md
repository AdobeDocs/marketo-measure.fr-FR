---
unique-page-id: 18874572
description: Duplication des enregistrements et [!DNL Marketo Measure] - [!DNL Marketo Measure]
title: Doublons d’enregistrements et  [!DNL Marketo Measure]
exl-id: e340100c-120a-4771-946d-336a1458da4e
feature: Tracking
source-git-commit: 9e672d0c568ee0b889461bb8ba6fc6333edf31ce
workflow-type: tm+mt
source-wordcount: '278'
ht-degree: 12%

---

# Duplication d’enregistrements et [!DNL Marketo Measure] {#duplicate-records-and-marketo-measure}

>[!NOTE]
>
>Des instructions spécifiant « [!DNL Marketo Measure] » peuvent s’afficher dans la documentation. Toutefois, votre gestion de la relation client (CRM) mentionne encore « Bizible ». Nous nous efforçons de mettre cela à jour. Notre nouvelle identité de marque (rebranding) sera bientôt répercutée dans votre CRM.

[!DNL Marketo Measure] utilise l’adresse électronique comme identifiant unique lors de la mise en correspondance des données avec un prospect ou un contact associé dans le CRM. Lorsque [!DNL Marketo Measure] trouve plusieurs Leads ou contacts avec la même adresse email, les mêmes données sont affichées sur tous les enregistrements. L’impact de cette situation survient lorsque vous signalez les Leads ou les contacts avec [!DNL Marketo Measure] et que vous pouvez incorrectement gonfler le nombre de personnes uniques ayant des points de contact d’achat.

À quoi cela ressemble-t-il dans les rapports [!DNL Marketo Measure] ?

_Exemple de rapport : [!DNL Marketo Measure] Personnes avec points de contact d’achat._

![](assets/1-1.png)

Vous pouvez constater, pour l’ID de personne [!DNL Marketo Measure] de kelsey@adobe.com, qu’il existe à la fois une piste et un contact avec cette adresse électronique. Dans ce rapport, deux Première touche sont rapportées, deux Touches de création de piste et deux interactions PostLC. Ces enregistrements en double partagent des informations de date et de point de contact, ce qui peut conduire à la conclusion qu’il s’agit de deux personnes différentes, bien qu’elles soient la même personne.

**Recommandation**

* Pour optimiser le retour dans vos rapports, nous vous recommandons d’utiliser un outil de déduplication dans votre CRM afin de vous assurer que vous ne créez que de nouveaux enregistrements nets et uniques. Vous pouvez le faire avec votre outil d’automatisation du marketing ou avec un logiciel distinct installé dans votre CRM. [!DNL Marketo Measure] ne déduplique pas automatiquement les enregistrements et ne propose pas ce service par le biais de notre logiciel.
* Une autre option consiste à fusionner manuellement les enregistrements lorsque vous identifiez des doublons. Ce processus peut être fastidieux et chronophage, mais la production de rapports précis en vaut la peine.
