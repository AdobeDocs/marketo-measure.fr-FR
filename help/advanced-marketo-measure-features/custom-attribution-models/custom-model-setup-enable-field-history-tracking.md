---
unique-page-id: 18874777
description: Configuration de modèle personnalisé - Activation du suivi de l’historique des champs -  [!DNL Marketo Measure]
title: Configuration de modèle personnalisé - Activation du suivi de l’historique des champs
exl-id: 70328e67-051b-4864-891b-b251e49859c2
feature: Custom Models
source-git-commit: 915e9c5a968ffd9de713b4308cadb91768613fc5
workflow-type: ht
source-wordcount: '312'
ht-degree: 100%

---

# Configuration de modèle personnalisé : activation du suivi de l’historique des champs {#custom-model-setup-enable-field-history-tracking}

## Pourquoi et quand activer le suivi de l’historique des champs {#why-and-when-to-enable-field-history-tracking}

Si vous décidez d’inclure un champ personnalisé en tant qu’étape dans votre modèle d’attribution personnalisé, le suivi de l’historique des champs **doit être activé** pour ce champ. L’activation du suivi de l’historique des champs permet à [!DNL Salesforce] d’effectuer le suivi de chaque modification du champ personnalisé en créant un enregistrement dans la table de suivi de l’historique. [!DNL Marketo Measure] peut télécharger cette table et utiliser ces informations pour mesurer l’heure et le jour d’une « transition ». Sans suivi de l’historique de champs, [!DNL Marketo Measure] ne peut pas effectuer le suivi des modifications liées à ce champ.

Si seules les étapes de [!UICONTROL statut de prospect] et d’opportunité sont utilisées dans le modèle personnalisé, il n’est pas nécessaire d’activer le suivi de l’historique des champs, car le suivi est effectué automatiquement en tant que transition d’étape.

Pour activer le suivi de l’historique des champs, suivez les instructions ci-dessous.

## Activer le suivi de l’historique des champs {#enable-field-history-tracking}

>[!NOTE]
>
>Pour apporter ces modifications aux champs de l’objet Prospect/Contact/Opportunité, vous devez être un administrateur ou une administratrice système.

1. Accédez à l’objet dans lequel se trouve le champ personnalisé et cliquez sur le bouton **[!UICONTROL Définir le suivi de l’historique]**.

   ![](assets/1.png)

1. Sélectionnez les champs sur lesquels vous souhaitez effectuer le suivi des modifications.

   ![](assets/2.png)

[!DNL Marketo Measure] ne peut réimporter un enregistrement que s’il détecte que l’enregistrement a récemment été modifié. Les champs de formule ne modifient pas techniquement un enregistrement lorsqu’il change, puisqu’il effectue le calcul en arrière-plan. Nous avons rencontré des problèmes lorsqu’une règle est ignorée, car [!DNL Marketo Measure] ne détectait pas le changement d’enregistrement. Il est donc conseillé de **ne pas utiliser de champs de formule dans les définitions de règle**. La solution consiste à créer un champ de texte et à utiliser un workflow pour renseigner ce champ avec la valeur appropriée ou le calcul approprié chaque fois que l’enregistrement est modifié ou qu’il correspond aux critères. Tous les enregistrements doivent ainsi être modifiés de sorte que le workflow puisse fonctionner rétroactivement sur les anciens enregistrements.
