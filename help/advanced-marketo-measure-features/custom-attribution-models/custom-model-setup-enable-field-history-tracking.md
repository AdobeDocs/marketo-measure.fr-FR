---
unique-page-id: 18874777
description: Configuration de modèle personnalisé - Activer le suivi de l’historique des champs - [!DNL Marketo Measure] - Documentation du produit
title: Configuration de modèle personnalisé - Activation du suivi de l’historique des champs
exl-id: 70328e67-051b-4864-891b-b251e49859c2
source-git-commit: b59c79236d3e324e8c8b07c5a6d68bd8176fc8a9
workflow-type: tm+mt
source-wordcount: '315'
ht-degree: 0%

---

# Configuration de modèle personnalisé : Activation du suivi de l’historique des champs {#custom-model-setup-enable-field-history-tracking}

## Pourquoi et quand activer le suivi de l’historique des champs {#why-and-when-to-enable-field-history-tracking}

Si vous décidez d’inclure un champ personnalisé en tant qu’étape dans votre modèle d’attribution personnalisé, le suivi de l’historique des champs **doit être activé** pour ce champ. L’activation du suivi de l’historique des champs permet [!DNL Salesforce] pour effectuer le suivi à chaque modification du champ personnalisé en créant un enregistrement dans la table Suivi de l’historique . [!DNL Marketo Measure] Vous pouvez télécharger ce tableau et utiliser ces informations pour mesurer l’heure et le jour d’une &quot;transition&quot;. Sans suivi de l&#39;historique des champs, [!DNL Marketo Measure] ne peut pas effectuer le suivi des modifications liées à ce champ.

Si uniquement [!UICONTROL État de piste] Pour que les étapes d’opportunité soient utilisées dans le modèle personnalisé, il n’est pas nécessaire d’activer le suivi de l’historique des champs, car il sera automatiquement suivi en tant que transition d’étape.

Pour activer le suivi de l’historique des champs, suivez les instructions ci-dessous.

## Activation du suivi de l’historique des champs {#enable-field-history-tracking}

>[!NOTE]
>
>Pour apporter ces modifications aux champs de l’objet Lead/Contact/Opportunity, vous devez être un administrateur système.

1. Accédez à l’objet dans lequel se trouve le champ personnalisé et cliquez sur le bouton **[!UICONTROL Définir le suivi de l’historique]** bouton .

   ![](assets/1.png)

1. Sélectionnez les champs sur lesquels vous souhaitez effectuer le suivi des modifications.

   ![](assets/2.png)

[!DNL Marketo Measure] ne peut réimporter un enregistrement que s’il détecte que l’enregistrement a récemment été modifié. D&#39;un point de vue technique, les champs de formule ne modifient pas un enregistrement lorsqu&#39;il change, puisqu&#39;il effectue le calcul en arrière-plan. Nous avons rencontré des problèmes lorsqu’une règle est ignorée car [!DNL Marketo Measure] n’ayant pas vu le changement d’enregistrement, il est conseillé de **ne pas utiliser de champs de formule dans les définitions de règle**. La solution consiste à créer un champ de texte et à utiliser un workflow pour renseigner ce champ avec la valeur ou le calcul appropriés chaque fois que l’enregistrement est modifié ou adapté aux critères. Cela nécessite que tous les enregistrements soient modifiés afin que le workflow puisse fonctionner rétroactivement sur les anciens enregistrements.
