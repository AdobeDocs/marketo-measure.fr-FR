---
unique-page-id: 18874562
description: Points de contact PostLC et engagement au prospect - Marketo Measure - Documentation du produit
title: Points de contact PostLC et engagement des prospects
exl-id: 3ee5c571-195e-46c7-b150-fedcbc3614cb
feature: Touchpoints
source-git-commit: 9e672d0c568ee0b889461bb8ba6fc6333edf31ce
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 3%

---

# Points de contact PostLC et engagement des prospects {#postlc-touchpoints-and-lead-engagement}

[!DNL Marketo Measure] Les points de contact Création après piste (PostLC) sont disponibles pour les clients qui utilisent des modèles d’attribution multipoints (forme W et supérieure). Lorsqu’un prospect ou un contact revient sur votre site Web et continue de remplir des formulaires, ces envois de formulaire sont enregistrés en tant que points de contact PostLC. Ces points de contact vous permettent de voir quel contenu pousse les pistes à continuer à interagir avec votre site, longtemps après leur première conversion. Les points de contact PostLC partagent le crédit d’attribution avec tous les points de contact intermédiaires au sein d’une opportunité ; un crédit d’attribution de 10 % est attribué aux points de contact intermédiaires et est réparti de manière égale entre toutes les touches.

![](assets/1.png)

Vous pouvez ajuster le nombre de points de contact PostLC affichés dans [!DNL SFDC]. En règle générale, il est recommandé de pousser jusqu’à cinq points de contact PostLC ; chaque point de contact atteint 1 Ko dans [!DNL SFDC].

>[!NOTE]
>
>Vous trouverez des instructions sur la façon de régler les paramètres des points de contact PostLC à la fin de cet article.

Les points de contact PostLC sont dynamiques. Comme un prospect ou un contact continue à envoyer des formulaires PostLC, [!DNL Marketo Measure] met à jour les points de contact PostLC dans votre gestion de la relation client afin de vous présenter les envois de formulaire les plus récents. Plus précisément, si vous avez défini une limite de 5 points de contact PostLC, [!DNL Marketo Measure] poussera toujours les cinq points de contact _le plus récent_ vers votre CRM.  Dans cet exemple, la limite de ce compte PostLC a été fixée à quatre points de contact. Ce prospect a déjà atteint le nombre maximal de points de contact PostLC qu’il peut avoir dans votre gestion de la relation client. La dernière touche PostLC était sur 2/6/2018. Si cette personne devait remplir un autre formulaire le jour suivant, [!DNL Marketo Measure] supprimera le premier point de contact PostLC de 11/9/2017 pour ajouter le dernier point de contact de 2/7/2018.

![](assets/2.png)

>[!NOTE]
>
>[!DNL Marketo Measure] ne met à jour que les points de contact PostLC sur le prospect ou le contact, et ne met pas à jour les points de contact d’attribution PostLC sur une opportunité. Tous les points de contact PostLC appropriés sur un contact sont inclus dans l’opportunité.

## Comment modifier les paramètres des points de contact PostLC {#how-to-change-postlc-touchpoint-settings}

Pour régler les paramètres des points de contact PostLC pour vos Leads ou contacts, suivez les instructions ci-dessous.

**Pistes**

1. Connectez-vous à votre compte [!DNL Marketo Measure] à l’adresse [experience.adobe.com/marketo-measure](https://experience.adobe.com/marketo-measure){target="_blank"} et accédez à [!UICONTROL Paramètres].

1. Sous CRM, Sélectionnez **[!UICONTROL Leads]**.

1. Saisissez le nombre de points de contact postLC que vous souhaitez transmettre à vos pistes et cliquez sur **[!UICONTROL Enregistrer]**.

   ![](assets/3.png)

**Contacts**

1. Connectez-vous à votre compte [!DNL Marketo Measure] à l’adresse [experience.adobe.com/marketo-measure](https://experience.adobe.com/marketo-measure){target="_blank"} et accédez à [!UICONTROL Paramètres].

1. Sous CRM, Sélectionnez **[!UICONTROL Contacts]**.

1. Saisissez le nombre de points de contact postLC que vous souhaitez transmettre à vos contacts et cliquez sur **[!UICONTROL Enregistrer]**.

   ![](assets/4.png)
