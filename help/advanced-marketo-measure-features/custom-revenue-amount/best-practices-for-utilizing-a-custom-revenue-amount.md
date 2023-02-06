---
description: Bonnes pratiques relatives à l’utilisation d’un montant de recettes personnalisé - [!DNL Marketo Measure] - Documentation du produit
title: Bonnes pratiques relatives à l’utilisation d’un montant de recettes personnalisé
exl-id: 553bd75a-512a-4733-a24b-8112eb420afc
source-git-commit: b59c79236d3e324e8c8b07c5a6d68bd8176fc8a9
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 0%

---

# Bonnes pratiques relatives à l’utilisation d’un montant de recettes personnalisé {#best-practices-for-utilizing-a-custom-revenue-amount}

## APERÇU {#overview}

Les principales fonctionnalités de [!DNL Marketo Measure] est la capacité d’attribuer un crédit de recettes aux points de contact marketing tout au long du parcours de l’acheteur. La clé d’une attribution de recettes précise est la possibilité pour [!DNL Marketo Measure] pour référencer le montant de recettes correct sur une opportunité, qui, à son tour, est réparti entre les points de contact marketing via les différents modèles d’attribution.

Sauf indication contraire, durant la mise en oeuvre, votre [!DNL Marketo Measure] est définie pour référencer le montant d’opportunité standard (par défaut SFDC) pour l’attribution des recettes. Cependant, pour de nombreux [!DNL Marketo Measure] , ce champ ne reflète pas le montant exact des recettes pour les opportunités. Dans ces cas, [!DNL Marketo Measure] offre la possibilité de configurer un montant de recettes personnalisé pour [!DNL Marketo Measure] pour référencer et distribuer les points de contact d’attribution.

## Bonne pratique {#best-practice}

Lors de la configuration d’un montant de recettes personnalisé, tenez compte des bonnes pratiques suivantes pour vous assurer que votre [!DNL Marketo Measure] les données d’attribution sont précises et cohérentes !

À retenir :

* Sélectionnez le champ de recettes qui est précis et utilisé pour toutes les opportunités .
   * ARR ou Valeur totale du contrat recommandé
* Ne pas utiliser de champ de formule
* Si vous utilisez un montant de recettes personnalisé pour les conversions de devise, la variable [!UICONTROL Marketo Measure : plusieurs devises] La fonctionnalité est la méthode préférée.
   * Le [!DNL Marketo Measure] La fonctionnalité de plusieurs devises fait référence aux taux de conversion définis dans [!DNL Salesforce] pour assurer au mieux l’alignement entre les conversions de devises. Vous pouvez ainsi continuer à utiliser le &quot;Montant&quot; standard (par défaut de la collecte de données régionale) ou tout autre champ de montant personnalisé relatif à la variable [!DNL Salesforce] taux de conversion.
* Si vous mettez à jour le champ Montant que vous souhaitez [!DNL Marketo Measure] pour effectuer des références, utilisez le chargeur de données pour mettre à jour les opportunités antérieures afin de vous assurer que vos données de recettes sont cohérentes et que le champ approprié est renseigné via le workflow.

## Bonne pratique pour la maintenance {#best-practice-for-maintenance}

L’examen annuel de la configuration du montant des recettes vous permet de vous assurer que vos données d’attribution sont exactes et conformes au reste des rapports sur les recettes de votre entreprise.

Si vous utilisez un montant de recettes personnalisé, vérifiez votre configuration de recettes comme suit.

* Dans votre [!DNL Marketo Measure] , accédez au[!UICONTROL Opportunités]section &#39; sous CRM
* Identifiez le [!UICONTROL Montant d’opportunité personnalisé] Champ, ici votre [!UICONTROL API de montant des recettes personnalisé] doit être répertorié
* Confirmez qu’il s’agit toujours du bon champ.
* Consultez également votre [!DNL Salesforce] L’administrateur confirme que le workflow Montant des recettes personnalisées dans [!DNL Salesforce] est toujours en cours d’exécution

Outre une révision annuelle, certaines modifications organisationnelles peuvent indiquer la nécessité de passer en revue la configuration du montant des recettes...

* Chiffre d’affaires de votre équipe marketing
* Modifications du champ Recettes personnalisées
* Changements de l’organisation dans la manière dont les recettes sont rapportées

>[!MORELIKETHIS]
>
>* [Utilisation d’un champ de montant des recettes personnalisé](/help/advanced-marketo-measure-features/custom-revenue-amount/using-a-custom-revenue-amount-field.md)
>* [Utilisation du chargeur de données pour mettre à jour le champ Montant personnalisé](/help/advanced-marketo-measure-features/custom-revenue-amount/using-data-loader-to-update-marketo-measure-custom-amount-field.md)
>* [Présentation de plusieurs devises](/help/advanced-marketo-measure-features/multi-currency/overview.md)
>* [Paramètres à plusieurs devises](/help/advanced-marketo-measure-features/multi-currency/settings.md)

