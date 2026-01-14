---
description: Recommandations relatives à l’utilisation d’un montant de revenu personnalisé pour les utilisateurs de Marketo Measure
title: Bonnes pratiques relatives à l’utilisation d’un montant de recettes personnalisé
exl-id: 553bd75a-512a-4733-a24b-8112eb420afc
feature: Custom Revenue Amount
source-git-commit: fcd8e276c85669ddf12bd7404fb12d3e99b2642a
workflow-type: tm+mt
source-wordcount: '436'
ht-degree: 7%

---

# Bonnes pratiques relatives à l’utilisation d’un montant de recettes personnalisé {#best-practices-for-utilizing-a-custom-revenue-amount}

## Vue d’ensemble {#overview}

La fonctionnalité principale de [!DNL Marketo Measure] est la possibilité d’affecter un crédit de revenu aux points de contact marketing sur l’ensemble du parcours de l’acheteur. La clé d’une attribution précise du chiffre d’affaires est la possibilité pour les [!DNL Marketo Measure] de référencer le montant correct du chiffre d’affaires sur une opportunité, qui à son tour est distribué entre les points de contact marketing via les différents modèles d’attribution.

Sauf indication contraire lors de la mise en œuvre, votre instance [!DNL Marketo Measure] est définie pour référencer le montant standard de l’opportunité (valeur par défaut de SFDC) pour l’attribution du chiffre d’affaires. Cependant, pour de nombreux comptes [!DNL Marketo Measure], ce champ ne reflète pas le montant exact des revenus pour les opportunités. Dans ces instances, [!DNL Marketo Measure] offre la possibilité de configurer un montant de chiffre d’affaires personnalisé pour que les [!DNL Marketo Measure] puissent le référencer et le distribuer sur les points de contact d’attribution (BAT).

## Bonne pratique {#best-practice}

Lors de la configuration d’un montant de chiffre d’affaires personnalisé, tenez compte des bonnes pratiques suivantes pour vous assurer que vos données d’attribution [!DNL Marketo Measure] sont exactes et cohérentes.

Points à retenir :

* Sélectionnez le champ de chiffre d’affaires précis et utilisé pour toutes les opportunités
   * ARR ou valeur totale du contrat est recommandé
* Ne pas utiliser de champ de formule
* Si vous utilisez un montant de revenu personnalisé pour les conversions de devises, la fonctionnalité [!UICONTROL Marketo Measure Multiple Currencies] est la méthode préférée à la place.
   * La fonctionnalité [!DNL Marketo Measure] plusieurs devises fait référence aux taux de conversion établis dans [!DNL Salesforce] pour garantir au mieux l’alignement entre les conversions de devises. Vous pouvez ainsi continuer à utiliser le « Montant » standard (par défaut SFDC) ou tout autre champ de montant personnalisé lié aux taux de conversion de [!DNL Salesforce].
* Si vous mettez à jour le champ Montant que vous souhaitez [!DNL Marketo Measure] référencer, utilisez le chargeur de données pour mettre à jour les opportunités antérieures afin de vous assurer que les données relatives au chiffre d’affaires sont cohérentes et que le champ approprié est renseigné via le workflow

## Bonne pratique de maintenance {#best-practice-for-maintenance}

En examinant chaque année la configuration du montant du chiffre d’affaires, vous vous assurerez que vos données d’attribution sont exactes et alignées sur le reste des rapports sur le chiffre d’affaires de votre entreprise.

Si vous utilisez un montant de revenu personnalisé, vérifiez la configuration de votre revenu comme suit.

* Dans votre compte [!DNL Marketo Measure], accédez à la section « [!UICONTROL  Opportunités ] sous CRM
* Identifiez le champ [!UICONTROL Montant de l’opportunité personnalisé] où votre champ [!UICONTROL API de montant du chiffre d’affaires personnalisé] doit être répertorié
* Vérifiez que ce champ est toujours correct
* Demandez également à votre administrateur [!DNL Salesforce] de confirmer que le workflow du montant du chiffre d’affaires personnalisé dans [!DNL Salesforce] est toujours en cours d’exécution

Outre une révision annuelle, certains changements organisationnels peuvent signaler la nécessité de revoir la configuration de votre montant de revenus...

* Changements au sein de votre équipe marketing
* Modifications apportées au champ Revenu personnalisé
* Modifications de l’organisation dans la manière dont le chiffre d’affaires est déclaré

>[!MORELIKETHIS]
>
>* [Utilisation d’un champ de montant du revenu personnalisé](/help/channel-tracking-and-setup/using-a-custom-revenue-amount-field.md)
>* [Utilisation du chargeur de données pour mettre à jour le champ de montant personnalisé](/help/channel-tracking-and-setup/using-data-loader-to-update-marketo-measure-custom-amount-field.md)
>* [Présentation de la fonctionnalité multidevise](/help/channel-tracking-and-setup/overview.md)
>* [Paramètres multidevises](/help/channel-tracking-and-setup/settings.md)
