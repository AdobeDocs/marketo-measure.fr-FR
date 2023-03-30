---
unique-page-id: 18874793
description: Utilisation d’un champ de montant des recettes personnalisé - [!DNL Marketo Measure] - Documentation du produit
title: Utilisation d’un champ de montant de recettes personnalisé
exl-id: 517ea4f9-aa83-48d0-8ce7-003f4a907430
source-git-commit: 51397a02872035fef41d308c1f855bcaecc29c4e
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 3%

---

# Utilisation d’un champ de montant de recettes personnalisé {#using-a-custom-revenue-amount-field}

Par défaut, les points de contact d’attribution de l’acheteur extraient le montant de l’opportunité de l’un des deux champs suivants :

* Montant (par défaut SFDC)
* [!DNL Marketo Measure] Montant de l&#39;opportunité (personnalisé)

Si vous utilisez un champ Montant personnalisé pour vos opportunités, nous devrons configurer un workflow afin de calculer les Recettes du point de contact de l’acheteur. Cela nécessite des connaissances plus avancées sur les [!DNL Salesforce], il peut donc nécessiter l’aide de votre administrateur SFDC.

À partir de maintenant, nous aurons besoin des informations suivantes :

* Nom de l’API de votre champ Montant

A partir de là, nous allons commencer à créer le workflow.

1. Accédez à **[!UICONTROL Configuration]** > **[!UICONTROL Créer]** > **[!UICONTROL Processus et approbations]** > **[!UICONTROL Règles de workflow]**.

   ![](assets/1.jpg)

1. Sélectionner **[!UICONTROL Nouvelle règle]**, définissez l’objet sur &quot;Opportunité&quot; et cliquez sur **[!UICONTROL Suivant]**.

   ![](assets/2.jpg)

   ![](assets/3.jpg)

1. Configurez le workflow. Définissez le nom de la règle sur &quot;Mettre à jour&quot;. [!DNL Marketo Measure] Montant de l&#39;opportunité.&quot; Définissez le critère d’évaluation sur &quot;Créé&quot; et chaque fois qu’il est modifié. Pour les critères de règle, sélectionnez votre champ Montant personnalisé et choisissez l’ opérateur [!UICONTROL comme &quot;Not Equal To&quot;] et laissez le champ &quot;Valeur&quot; vide.

   ![](assets/4.jpg)

1. Ajoutez une action de workflow. Définissez cette liste de sélection sur &quot;[!UICONTROL Nouvelle mise à jour des champs].&quot;

   ![](assets/5.jpg)

1. Vous y trouverez les informations sur les champs. Dans le champ &quot;Nom&quot;, il est recommandé d&#39;utiliser ce nom : &quot;[!DNL Marketo Measure] Montant Opp.&quot; Le &quot;Nom unique&quot; est automatiquement renseigné à partir du champ &quot;Nom&quot;. Dans la liste de sélection &quot;Champ à mettre à jour&quot;, sélectionnez &quot;[!DNL Marketo Measure] Montant de l&#39;opportunité.&quot; Après avoir sélectionné le champ, cochez la case &quot;Réévaluer les règles de workflow après modification du champ&quot;. Dans &quot;Spécifier la nouvelle valeur du champ&quot;, sélectionnez &quot;Utiliser une formule pour définir la nouvelle valeur&quot;. Dans la zone vide, déposez le nom de l’API de votre champ Montant personnalisé. Cliquez sur **[!UICONTROL Enregistrer]**.

   ![](assets/6.png)

1. Vous serez redirigé vers une page de cumul pour votre workflow, assurez-vous d’&quot;activer&quot; et vous serez opérationnel. Pour activer, cliquez sur **Modifier** en regard de votre nouveau workflow, puis cliquez sur **Activer**.

   Une fois ces étapes terminées, les opportunités doivent être mises à jour afin de déclencher le workflow pour que la nouvelle valeur de la variable [!UICONTROL opportunité personnalisée] champ .

   Pour ce faire, exécutez vos opportunités via Data Loader dans SFDC. Pour plus d’informations sur l’utilisation de Data Loader dans [cet article](/help/advanced-marketo-measure-features/custom-revenue-amount/using-data-loader-to-update-marketo-measure-custom-amount-field.md).

Si vous avez des questions, n’hésitez pas à contacter l’équipe de compte d’Adobe (votre gestionnaire de compte) ou [[!DNL Marketo] Assistance](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"}.
