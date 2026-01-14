---
description: Instructions de mise en page destinées aux utilisateurs de Marketo Measure
title: Instructions de disposition de page
exl-id: 627377f0-d0cf-448c-a7b5-7eb5634b9627
feature: Salesforce
source-git-commit: fcd8e276c85669ddf12bd7404fb12d3e99b2642a
workflow-type: tm+mt
source-wordcount: '855'
ht-degree: 92%

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

   ![1. Cliquez sur Mises en page.](assets/marketo-salesforce-7.jpg)

1. Cliquez sur **[!UICONTROL Modifier]** en regard de la disposition de page que vous souhaitez mettre à jour.

   ![1. Cliquez sur Modifier en regard de la mise en page souhaitée](assets/marketo-salesforce-1.jpg)

1. Dans l’option [!UICONTROL champs], sélectionnez le champ **[!UICONTROL Activer Buyer Touchpoints]** et faites-le glisser à l’emplacement de votre choix sur la page. Ajoutez ensuite les champs **[!UICONTROL Date de début du point de contact]** et **[!UICONTROL Date de fin du point de contact]**.

   ![1. Dans l’option Champs , sélectionnez Activer les points de contact de l’acheteur](assets/bizible-full-1.png)

1. Ensuite, dans la partie supérieure de la page, cliquez sur l’option « [!UICONTROL Boutons] » dans le menu de recherche rapide.

1. Faites glisser le bouton **[!UICONTROL Mettre à jour en bloc la date du point de contact]** dans votre section de boutons personnalisés.

   ![1. Faites glisser le bouton Date de point de contact de mise à jour en bloc vers votre ](assets/bizible-taxonomy-1.png) personnalisé

1. Cliquez sur **[!UICONTROL Enregistrer]**.

   >[!NOTE]
   >
   >Si vous utilisez plusieurs types d’enregistrements de campagne, vous devez mettre à jour les valeurs de liste de sélection pour le champ **[!UICONTROL Activer Buyer Touchpoints]**. Consultez [cet article](/help/channel-tracking-and-setup/configurations-record-types.md) pour obtenir des instructions.

## Prospects {#leads}

1. Dans l’option Créer, sélectionnez **[!UICONTROL Prospects]**.

1. Cliquez sur **[!UICONTROL Dispositions de page]**.

1. Cliquez sur **[!UICONTROL Modifier]** en regard de la disposition de page que vous souhaitez mettre à jour. Gardez à l’esprit que plusieurs dispositions de page peuvent contenir les sections Buyer Touchpoints.

1. Cliquez sur l’option de page VisualForce à gauche dans le menu de recherche rapide.

1. Créez une section et nommez-la « Buyer Touchpoints ».

1. Faites glisser la page VisualForce **[!UICONTROL Liste connexe Prospect Marketo Measure]** dans votre section de disposition de page.

   ![1. Faites glisser la page Marketo Measure Lead Related List VisualForce dans ](assets/connect-salesforce-1.png)

1. Cliquez sur la clé à molette dans la page [!DNL VisualForce], définissez la hauteur sur 100 et activez les barres de défilement.

1. De retour dans le menu, sélectionnez la section [!UICONTROL Applications de zone de travail] et créez une section appelée « Insights Marketo Measure » sous la section Points de contact [!DNL VisualForce] que vous avez créée.

1. Faites glisser l’application de zone de travail [!DNL Marketo Measure Insights] dans cette section nouvellement créée. Cliquez sur **Enregistrer**. Il est parfois nécessaire d’enregistrer d’abord la disposition de page avant de la déposer dans l’application de zone de travail, car Salesforce ne la reconnaît pas instantanément. Ainsi, après avoir créé la section, enregistrez la disposition de page, puis modifiez à nouveau pour faire glisser l’application de zone de travail dans cette section. Cela s’applique à chaque objet.

   >[!NOTE]
   >
   >Pour que l’application de zone de travail [!DNL Marketo Measure Insights] fonctionne, [les autorisations doivent être correctement configurées](/help/configuration-and-setup/marketo-measure-insights-configuration.md).

Si vous utilisez la fonctionnalité ABM [!DNL Marketo Measure], [cliquez ici pour obtenir des instructions de disposition de page supplémentaires](/help/channel-tracking-and-setup/account-based-marketing-overview.md).

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

   ![1. Trier Par : Date Du Point De Contact, Croissant.](assets/marketo-salesforce-15.jpg)

1. Développez l’option Boutons et désélectionnez **[!UICONTROL Nouveau]**.

   ![1. Développez l’option Boutons et désélectionnez Nouveau ](assets/marketo-salesforce-12.png).

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

Si vous utilisez la fonctionnalité ABM [!DNL Marketo Measure], passez en revue les [instructions de disposition de page supplémentaires](/help/channel-tracking-and-setup/account-based-marketing-overview.md).
