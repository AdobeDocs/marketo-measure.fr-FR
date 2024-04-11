---
unique-page-id: 18874799
description: Instructions de disposition de page -  [!DNL Marketo Measure]
title: Instructions de disposition de page
exl-id: 627377f0-d0cf-448c-a7b5-7eb5634b9627
feature: Salesforce
source-git-commit: 9e672d0c568ee0b889461bb8ba6fc6333edf31ce
workflow-type: ht
source-wordcount: '833'
ht-degree: 100%

---

# Instructions de disposition de page {#page-layout-instructions}

>[!NOTE]
>
>Des instructions spécifiant « [!DNL Marketo Measure] » peuvent s’afficher dans la documentation. Toutefois, votre gestion de la relation client (CRM) mentionne encore « Bizible ». Nous nous efforçons de mettre cela à jour. Notre nouvelle identité de marque (rebranding) sera bientôt répercutée dans votre CRM.

Pour afficher facilement des données [!DNL Marketo Measure], il est recommandé de mettre à jour les dispositions de page pour les objets [!UICONTROL Compte], [!UICONTROL Contact], [!UICONTROL Prospect], [!UICONTROL Opportunité] et [!UICONTROL Campagne]. Les instructions sont détaillées pour chaque disposition de page d’objet ci-dessous.

Pour commencer, accédez à vos paramètres de configuration de [!DNL Salesforce] et recherchez l’onglet [!UICONTROL Personnaliser].

## Objet de campagne {#campaign-object}

Il est recommandé d’ajouter les champs [!DNL Marketo Measure] à votre campagne SFDC pour votre sandbox uniquement. Les champs peuvent être utilisés pour tester la génération du point de contact. En production, il est recommandé de n’ajouter que le bouton Mettre à jour en bloc la date du point de contact [!DNL Marketo Measure]. Il n’est pas recommandé d’ajouter les champs [!DNL Marketo Measure] en production puisque vous pouvez créer une règle de synchronisation de campagne.

1. Dans l’option Créer, sélectionnez **[!UICONTROL Campagnes]**.

1. Cliquez sur **[!UICONTROL Dispositions de page]**.

   ![](assets/1-1.jpg)

1. Cliquez sur **[!UICONTROL Modifier]** en regard de la disposition de page que vous souhaitez mettre à jour.

   ![](assets/2-1.jpg)

1. Dans l’option [!UICONTROL champs], sélectionnez le champ **[!UICONTROL Activer Buyer Touchpoints]** et faites-le glisser à l’emplacement de votre choix sur la page. Ajoutez ensuite les champs **[!UICONTROL Date de début du point de contact]** et **[!UICONTROL Date de fin du point de contact]**.

   ![](assets/3-2.png)

1. Ensuite, dans la partie supérieure de la page, cliquez sur l’option « [!UICONTROL Boutons] » dans le menu de recherche rapide.

1. Faites glisser le bouton **[!UICONTROL Mettre à jour en bloc la date du point de contact]** dans votre section de boutons personnalisés.

   ![](assets/4-1.jpg)

1. Cliquez sur **[!UICONTROL Enregistrer]**.

   >[!NOTE]
   >
   >Si vous utilisez plusieurs types d’enregistrements de campagne, vous devez mettre à jour les valeurs de liste de sélection pour le champ **[!UICONTROL Activer Buyer Touchpoints]**. Consultez [cet article](/help/channel-tracking-and-setup/offline-channels/configurations-for-multiple-campaign-record-types.md) pour obtenir des instructions.

## Prospects {#leads}

1. Dans l’option Créer, sélectionnez **[!UICONTROL Prospects]**.

1. Cliquez sur **[!UICONTROL Dispositions de page]**.

1. Cliquez sur **[!UICONTROL Modifier]** en regard de la disposition de page que vous souhaitez mettre à jour. Gardez à l’esprit que plusieurs dispositions de page peuvent contenir les sections Buyer Touchpoints.

1. Cliquez sur l’option de page VisualForce à gauche dans le menu de recherche rapide.

1. Créez une section et nommez-la « Buyer Touchpoints ».

   >[!NOTE]
   >
   >Sélectionnez le format « une colonne » pour chacune de ces sections.

1. Faites glisser la page VisualForce **[!UICONTROL Liste connexe Prospect Marketo Measure]** dans votre section de disposition de page.

   ![](assets/5-1.png)

1. Cliquez sur la clé à molette dans la page [!DNL VisualForce], définissez la hauteur sur 100 et activez les barres de défilement.

1. De retour dans le menu, sélectionnez la section [!UICONTROL Applications de zone de travail] et créez une section appelée « Insights Marketo Measure » sous la section Points de contact [!DNL VisualForce] que vous avez créée.

   >[!NOTE]
   >
   >Sélectionnez le format « une colonne » pour chacune de ces sections.

1. Faites glisser l’application de zone de travail [!DNL Marketo Measure Insights] dans cette section nouvellement créée. Cliquez sur **Enregistrer**. Il est parfois nécessaire d’enregistrer d’abord la disposition de page avant de la déposer dans l’application de zone de travail, car Salesforce ne la reconnaît pas instantanément. Ainsi, après avoir créé la section, enregistrez la disposition de page, puis modifiez à nouveau pour faire glisser l’application de zone de travail dans cette section. Cela s’applique à chaque objet.

   >[!NOTE]
   >
   >Pour que l’application de zone de travail [!DNL Marketo Measure Insights] fonctionne, [les autorisations doivent être correctement configurées](/help/configuration-and-setup/marketo-measure-insights-canvas-app/marketo-measure-insights-configuration.md).

   >[!TIP]
   >
   >La plupart des clientes et clients n’utilisent pas les champs qui se terminent par (FT) ou (LC), car il s’agit de champs hérités d’avant l’existence du point de contact [!DNL Marketo Measure] en tant qu’objet.

Si vous utilisez la fonctionnalité ABM [!DNL Marketo Measure], [cliquez ici pour obtenir des instructions de disposition de page supplémentaires](/help/advanced-marketo-measure-features/account-based-marketing/account-based-marketing-overview.md).

## Contacts {#contacts}

1. Dans l’option Créer, sélectionnez **[!UICONTROL Contacts]**.

1. Cliquez sur **[!UICONTROL Dispositions de page]**.

1. Sélectionnez la disposition de page que vous souhaitez modifier.

   Accédez à l’option Listes connexes dans le menu de recherche rapide et ajoutez la liste connexe **[!UICONTROL Buyer Touchpoints]**.

1. Cliquez sur l’icône en forme de clé à molette et ajoutez les colonnes suivantes dans cet ordre :

   * Buyer Touchpoint
   * Canal marketing
   * Source du point de contact
   * Nom de la campagne publicitaire
   * Position du point de contact
   * Date du point de contact

1. Trier par : Date du point de contact, Ascendant.

   ![](assets/6.jpg)

1. Développez l’option Boutons et désélectionnez **[!UICONTROL Nouveau]**.

   ![](assets/7.png)

1. Revenez à l’option [!UICONTROL Liste connexe] dans le menu et ajoutez maintenant la liste connexe **[!UICONTROL Buyer Attribution Touchpoint]**.

1. Cliquez sur l’icône en forme de clé à molette et ajoutez les colonnes suivantes dans cet ordre :

   * Point de contact d’attribution
   * Canal marketing
   * Opportunité
   * Nom de la campagne publicitaire
   * Type de point de contact
   * Position du point de contact
   * % d’attribution en W (_ou modèle d’attribution le plus robuste, tel que Chemin complet ou Personnalisé_)
   * Revenu en W (_ou modèle d’attribution le plus robuste, tel que Chemin complet ou Personnalisé_)
   * Date du point de contact

1. Triez par [!UICONTROL Date du point de contact] > [!UICONTROL Ascendant].

1. Développez la section Boutons et désélectionnez **[!UICONTROL Nouveau]**.

1. Cliquez sur **[!UICONTROL Enregistrer]**.

## Opportunités {#opportunities}

1. Dans l’option Créer, sélectionnez **[!UICONTROL Opportunités]**.

1. Cliquez sur **[!UICONTROL Dispositions de page]**.

1. Sélectionnez la disposition de page que vous souhaitez modifier.

1. Ajoutez la liste connexe **[!UICONTROL Buyer Attribution Touchpoint]** et cliquez sur la clé à molette pour ajouter les colonnes suivantes pour les opportunités :

   * Point de contact d’attribution
   * Canal marketing
   * Contact
   * Nom de la campagne publicitaire
   * Type de point de contact
   * Position du point de contact
   * % d’attribution en W (_ou modèle d’attribution le plus robuste, tel que Chemin complet ou Personnalisé_)
   * Revenu en W (_ou modèle d’attribution le plus robuste, tel que Chemin complet ou Personnalisé_)
   * Date du point de contact

1. Triez par [!UICONTROL Date du point de contact] > [!UICONTROL Ascendant].

1. Désélectionnez **[!UICONTROL Nouveau]** dans la section [!UICONTROL Boutons].

1. Cliquez sur **[!UICONTROL Enregistrer]**.

## Comptes {#accounts}

1. Dans l’option Créer, sélectionnez **[!UICONTROL Comptes]**.

1. Cliquez sur **[!UICONTROL Dispositions de page]**.

1. Sélectionnez la disposition de page que vous souhaitez modifier.

1. Ajoutez la liste connexe **[!UICONTROL Buyer Attribution Touchpoint]** et cliquez sur la clé à molette pour ajouter les colonnes suivantes :

   * Point de contact d’attribution
   * Canal marketing
   * Opportunité
   * Nom de la campagne publicitaire
   * Type de point de contact
   * Position du point de contact
   * % d’attribution en W (_ou modèle d’attribution le plus robuste, tel que Chemin complet ou Personnalisé_)
   * Revenu en W (_ou modèle d’attribution le plus robuste, tel que Chemin complet ou Personnalisé_)
   * Date du point de contact

1. Triez par Date du point de contact > Ascendant.

1. Désélectionnez **[!UICONTROL Nouveau]** dans la section [!UICONTROL Boutons].

1. Cliquez sur **[!UICONTROL Enregistrer]**.

Si vous utilisez la fonctionnalité ABM [!DNL Marketo Measure], passez en revue les [instructions de disposition de page supplémentaires](/help/advanced-marketo-measure-features/account-based-marketing/account-based-marketing-overview.md).
