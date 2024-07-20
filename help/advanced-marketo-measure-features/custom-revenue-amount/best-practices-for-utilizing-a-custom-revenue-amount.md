---
description: Bonnes pratiques pour l’utilisation d’un montant de recettes personnalisé - [!DNL Marketo Measure]
title: Bonnes pratiques relatives à l’utilisation d’un montant de recettes personnalisé
exl-id: 553bd75a-512a-4733-a24b-8112eb420afc
feature: Custom Revenue Amount
source-git-commit: 9e672d0c568ee0b889461bb8ba6fc6333edf31ce
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 7%

---

# Bonnes pratiques relatives à l’utilisation d’un montant de recettes personnalisé {#best-practices-for-utilizing-a-custom-revenue-amount}

## Vue d’ensemble {#overview}

La fonctionnalité principale de [!DNL Marketo Measure] est la possibilité d’attribuer un crédit de recettes aux points de contact marketing tout au long du parcours de l’acheteur. La clé d’une attribution de recettes exacte est la possibilité pour [!DNL Marketo Measure] de référencer le montant de recettes correct sur une opportunité, qui, à son tour, est réparti entre les points de contact marketing via les différents modèles d’attribution.

Sauf indication contraire durant la mise en oeuvre, votre instance [!DNL Marketo Measure] sera définie pour faire référence au montant d’opportunité standard (par défaut SFDC) pour l’attribution des recettes. Cependant, pour de nombreux comptes [!DNL Marketo Measure], ce champ ne reflète pas le montant exact des recettes pour les opportunités. Dans ces instances, [!DNL Marketo Measure] offre la possibilité de configurer un montant de recettes personnalisé pour [!DNL Marketo Measure] afin de référencer et de distribuer les points de contact d’attribution (BAT).

## Bonne pratique {#best-practice}

Lors de la configuration d’un montant de recettes personnalisé, gardez à l’esprit les bonnes pratiques suivantes pour vous assurer que vos données d’attribution [!DNL Marketo Measure] sont exactes et cohérentes !

Points à retenir :

* Sélectionnez le champ de recettes qui est précis et utilisé pour toutes les opportunités .
   * ARR ou Valeur totale du contrat recommandé
* Ne pas utiliser de champ de formule
* Si vous utilisez un montant de recettes personnalisé pour les conversions de devises, la fonctionnalité [!UICONTROL Marketo Measure Multiple Currencies] est la méthode préférée à la place.
   * La fonctionnalité [!DNL Marketo Measure] plusieurs devises fait référence aux taux de conversion établis dans [!DNL Salesforce] pour garantir au mieux l’alignement entre les conversions de devises. Cela vous permet de continuer à utiliser le &quot;Montant&quot; standard (par défaut de la collecte de données régionale), ou tout autre champ de montant personnalisé relatif aux taux de conversion [!DNL Salesforce].
* Si vous mettez à jour le champ Montant que vous souhaitez référencer [!DNL Marketo Measure], utilisez le chargeur de données pour mettre à jour les opportunités antérieures afin de vous assurer que vos données de recettes sont cohérentes et que le champ approprié est renseigné via le workflow.

## Bonne pratique de maintenance {#best-practice-for-maintenance}

L’examen annuel de la configuration du montant des recettes vous permet de vous assurer que vos données d’attribution sont exactes et conformes au reste des rapports sur les recettes de votre entreprise.

Si vous utilisez un montant de recettes personnalisé, vérifiez votre configuration de recettes comme suit.

* Dans votre compte [!DNL Marketo Measure], accédez à la section &#39;[!UICONTROL Opportunités]&#39; sous CRM
* Identifiez le champ [!UICONTROL Montant d’opportunité personnalisé], où votre champ [!UICONTROL  API de montant de recettes personnalisé] doit être répertorié.
* Confirmez qu’il s’agit toujours du bon champ.
* Demandez également à votre administrateur [!DNL Salesforce] de confirmer que le workflow Montant des recettes personnalisées dans [!DNL Salesforce] est toujours en cours d’exécution.

Outre une révision annuelle, certaines modifications organisationnelles peuvent indiquer la nécessité de passer en revue la configuration du montant des recettes...

* Changements au sein de votre équipe marketing
* Modifications du champ Recettes personnalisées
* Changements de l’organisation dans la manière dont les recettes sont rapportées

>[!MORELIKETHIS]
>
>* [Utilisation d’un champ Montant des recettes personnalisées](/help/advanced-marketo-measure-features/custom-revenue-amount/using-a-custom-revenue-amount-field.md)
>* [ Utilisation du chargeur de données pour mettre à jour le champ Montant personnalisé](/help/advanced-marketo-measure-features/custom-revenue-amount/using-data-loader-to-update-marketo-measure-custom-amount-field.md)
>* [Présentation de plusieurs devises](/help/advanced-marketo-measure-features/multi-currency/overview.md)
>* [Paramètres à plusieurs devises](/help/advanced-marketo-measure-features/multi-currency/settings.md)
