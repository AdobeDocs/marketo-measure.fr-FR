---
description: Découvrez comment les points de contact PostLC sont créés, mis à jour et limités pour les prospects et les contacts
title: Points de contact PostLC et engagement des prospects
exl-id: 3ee5c571-195e-46c7-b150-fedcbc3614cb
feature: Touchpoints
source-git-commit: fcd8e276c85669ddf12bd7404fb12d3e99b2642a
workflow-type: tm+mt
source-wordcount: '435'
ht-degree: 3%

---

# Points de contact PostLC et engagement des prospects {#postlc-touchpoints-and-lead-engagement}

[!DNL Marketo Measure] points de contact de la création post-lead (PostLC) sont disponibles pour les clients qui utilisent des modèles d’attribution multipoint (en W et supérieurs). Lorsqu’un prospect ou un contact revient sur votre site web et continue à remplir des formulaires, ces envois de formulaires s’enregistrent en tant que points de contact PostLC. Ces points de contact vous permettent de voir quel contenu incite les prospects à continuer à interagir avec votre site, longtemps après leur première conversion. Les points de contact PostLC partagent le crédit d’attribution avec tous les points de contact intermédiaires au sein d’une opportunité. Un crédit d’attribution de 10 % est attribué aux points de contact intermédiaires et est réparti de manière égale entre tous les contacts.

![Les points de contact de la création post-lead de Marketo Measure (PostLC) sont disponibles pour les clients qui utilisent &#x200B;](assets/additional-functionality-1.png)

Vous pouvez ajuster le nombre de points de contact PostLC affichés dans [!DNL SFDC]. En règle générale, nous vous recommandons de transmettre jusqu’à cinq points de contact PostLC ; chaque point de contact prend jusqu’à 1 Ko en [!DNL SFDC].

>[!NOTE]
>
>Vous trouverez des instructions sur la façon d’ajuster les paramètres de point de contact PostLC à la fin de cet article.

Les points de contact PostLC sont dynamiques. Lorsqu’un prospect ou un contact continue à envoyer des formulaires PostLC, [!DNL Marketo Measure] met à jour les points de contact PostLC dans votre CRM pour vous montrer leurs envois de formulaires les plus récents. Plus précisément, si vous avez défini une limite de 5 points de contact PostLC, [!DNL Marketo Measure] toujours transmettre les cinq points de contact _les plus récents_ à votre CRM.  Dans cet exemple, ce compte a défini sa limite PostLC sur quatre points de contact. Ce lead a déjà atteint le nombre maximal de points de contact PostLC qu’il peut avoir dans votre CRM. La dernière touche PostLC a eu lieu le 2/6/2018. Si cette personne devait remplir un autre formulaire le lendemain, [!DNL Marketo Measure] supprimerait le premier point de contact PostLC du 11/9/2017 pour ajouter le dernier point de contact du 2/7/2018.

Les points de contact ![PostLC) sont dynamiques. En tant que lead ou contact continuant à envoyer &#x200B;](assets/additional-functionality-2.png)

>[!NOTE]
>
>[!DNL Marketo Measure] met uniquement à jour les points de contact PostLC sur le lead ou le contact et ne met pas à jour les points de contact d’attribution PostLC sur une opportunité. Tous les points de contact PostLC pertinents d’un contact sont inclus dans l’opportunité.

## Modification des paramètres de point de contact PostLC {#how-to-change-postlc-touchpoint-settings}

Pour ajuster les paramètres de point de contact PostLC pour vos leads ou contacts, suivez les instructions ci-dessous.

**Leads**

1. Connectez-vous à votre compte [!DNL Marketo Measure] à l’adresse [experience.adobe.com/marketo-measure](https://experience.adobe.com/marketo-measure){target="_blank"} puis accédez à [!UICONTROL Paramètres].

1. Sous CRM, sélectionnez **[!UICONTROL Leads]**.

1. Saisissez le nombre de points de contact postLC que vous souhaitez intégrer à vos Leads et cliquez sur **[!UICONTROL Enregistrer]**.

   ![1. Saisissez le nombre de points de contact postLC sur lesquels vous souhaitez envoyer une notification push](assets/additional-functionality-3.png)

**Contacts**

1. Connectez-vous à votre compte [!DNL Marketo Measure] à l’adresse [experience.adobe.com/marketo-measure](https://experience.adobe.com/marketo-measure){target="_blank"} puis accédez à [!UICONTROL Paramètres].

1. Sous CRM, sélectionnez **[!UICONTROL Contacts]**.

1. Saisissez le nombre de points de contact postLC que vous souhaitez envoyer à vos contacts et cliquez sur **[!UICONTROL Enregistrer]**.

   ![1. Saisissez le nombre de points de contact postLC sur lesquels vous souhaitez envoyer une notification push](assets/additional-functionality-4.png)
