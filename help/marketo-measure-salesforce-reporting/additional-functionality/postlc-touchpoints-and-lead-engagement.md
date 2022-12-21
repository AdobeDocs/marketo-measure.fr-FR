---
unique-page-id: 18874562
description: Points de contact PostLC et engagement au prospect - Mesure Marketo - Documentation du produit
title: Points de contact PostLC et engagement au prospect
exl-id: 3ee5c571-195e-46c7-b150-fedcbc3614cb
source-git-commit: f13e55f009f33140ff36523212ed8b9ed5449a4d
workflow-type: tm+mt
source-wordcount: '393'
ht-degree: 0%

---

# Points de contact PostLC et engagement au prospect {#postlc-touchpoints-and-lead-engagement}

[!DNL Marketo Measure] Les points de contact Post-Lead Creation (PostLC) sont disponibles pour les clients utilisant des modèles d’attribution multi-touch (W-Shape et versions ultérieures). Lorsqu’un prospect ou un contact revient sur votre site web et continue de remplir des formulaires, ces envois de formulaire sont enregistrés en tant que points de contact PostLC. Ces points de contact vous permettent de voir quel contenu pousse les pistes à continuer à interagir avec votre site, longtemps après leur première conversion. Les points de contact PostLC partagent le crédit d’attribution avec tous les points de contact intermédiaires au sein d’une opportunité ; Le crédit d’attribution de 10 % est attribué aux points de contact intermédiaires et est réparti équitablement entre toutes les touches.

![](assets/1.png)

Vous pouvez ajuster le nombre de points de contact PostLC qui s’afficheront dans [!DNL SFDC]. En règle générale, il est recommandé de pousser jusqu’à cinq points de contact PostLC ; chaque point de contact prend 1 Ko dans [!DNL SFDC].

>[!NOTE]
>
>Vous trouverez des instructions sur la façon de régler les paramètres des points de contact PostLC à la fin de cet article.

Les points de contact PostLC sont dynamiques. Comme un prospect ou un contact continue à envoyer des formulaires PostLC, [!DNL Marketo Measure] mettra à jour les points de contact PostLC dans votre gestion de la relation client afin de vous présenter les derniers envois de formulaire. Plus précisément, si vous avez défini une limite de 5 points de contact PostLC, [!DNL Marketo Measure] toujours pousser le 5 _le plus récent_ points de contact vers votre CRM.  Dans cet exemple, la limite de ce compte PostLC a été fixée à quatre points de contact. Ce prospect a déjà atteint le nombre maximal de points de contact PostLC qu’il peut avoir dans votre CRM. La dernière touche PostLC était sur 2/6/2018. Si cette personne devait remplir un autre formulaire le jour suivant, [!DNL Marketo Measure] supprime le premier point de contact PostLC de 11/9/2017 afin d’ajouter le dernier point de contact de 2/7/2018.

![](assets/2.png)

>[!NOTE]
>
>[!DNL Marketo Measure] mettra uniquement à jour les points de contact PostLC sur le prospect ou le contact, et ne mettra pas à jour les points de contact d’attribution PostLC sur une opportunité. Tous les points de contact PostLC pertinents sur un contact seront inclus dans l’opportunité.

## Comment modifier les paramètres des points de contact PostLC {#how-to-change-postlc-touchpoint-settings}

Pour régler les paramètres des points de contact PostLC pour vos Leads ou contacts, suivez les instructions ci-dessous.

**Prospects**

1. Connectez-vous à [!DNL Marketo Measure] compte à l’adresse [experience.adobe.com/marketo-measure](https://experience.adobe.com/marketo-measure){target=&quot;_blank&quot;} et accédez à [!UICONTROL Paramètres].

1. Sous CRM, sélectionnez **[!UICONTROL Pistes]**.

1. Saisissez le nombre de points de contact postLC que vous souhaitez transmettre à vos pistes, puis cliquez sur **[!UICONTROL Enregistrer]**.

   ![](assets/3.png)

**Contacts**

1. Connectez-vous à [!DNL Marketo Measure] compte à l’adresse [experience.adobe.com/marketo-measure](https://experience.adobe.com/marketo-measure){target=&quot;_blank&quot;} et accédez à [!UICONTROL Paramètres].

1. Sous CRM, sélectionnez **[!UICONTROL Contacts]**.

1. Saisissez le nombre de points de contact postLC que vous souhaitez transmettre à vos contacts, puis cliquez sur **[!UICONTROL Enregistrer]**.

   ![](assets/4.png)
