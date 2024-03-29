---
description: Bonnes pratiques pour le mappage des étapes - [!DNL Marketo Measure]
title: Bonnes pratiques relatives au mappage des étapes
exl-id: 1ed380a1-4a3a-4761-b70f-cdf2e290329d
feature: Tracking, Custom Models
source-git-commit: 1a274c83814f4d729053bb36548ee544b973dff5
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 4%

---

# Bonnes pratiques relatives au mappage des étapes {#best-practices-for-stage-mapping}

## Vue d’ensemble {#overview}

La section Mappage des environnements intermédiaires de votre [!DNL Marketo Measure] le compte décrit les étapes qui [!DNL Marketo Measure] extrait automatiquement de votre gestion de la relation client et des étapes personnalisées que vous avez définies en cas d’utilisation du modèle d’attribution personnalisé. La validité de votre [!DNL Marketo Measure] Les données reposent sur l’ordre correct de ces étapes afin que [!DNL Marketo Measure] peut comprendre précisément votre entonnoir et la progression des enregistrements dans cet entonnoir.

Dans la section Mappage dans l’environnement intermédiaire de votre [!DNL Marketo Measure] vous verrez à la fois les étapes actives et inactives de votre CRM. Organisez toutes les scènes au mieux de vos capacités en fonction de la façon dont votre entonnoir se présente aujourd’hui.

Une autre fonctionnalité gérée dans cette section est les phases d’entonnoir, qui vous permettent d’ajouter des étapes à l’entonnoir sans appliquer d’attribution. Les phases d’entonnoir seront suivies comme points de contact et seront renseignées dans le champ Positions des points de contact de votre CRM. Ces étapes d’entonnoir seront également représentées dans divers panoramas de parcours dans [!DNL Marketo Measure] Découvrez-le.

## Meilleures pratiques {#best-practices}

Que vous évaluiez votre mappage dans l’environnement intermédiaire pour la première fois ou que vous veniez de vérifier l’ordre de votre entonnoir, il est important de garder à l’esprit les bonnes pratiques suivantes.

* L&#39;ordre est tout !
   * Considérer [!DNL Marketo Measure] extrait les étapes actives et inactives de votre CRM, puis confirme que toute étape pouvant être utilisée sur un prospect/contact ou opportunité est regroupée et ordonnée en conséquence.
* Lors de la définition d’une étape personnalisée, assurez-vous que le suivi de l’historique des champs est activé pour tous les champs utilisés pour définir l’étape.
* N’utilisez pas de champ de formule pour définir une étape personnalisée
   * Un champ booléen est la recommandation recommandée.
* Notez que la section Intervalle de piste ou Contact est divisée en Perdu, Ouvert et Converti ; vérifiez que les étapes se trouvent dans la section correspondante.
   * Le fait qu’une étape se trouve dans une section d’étape incorrecte peut entraîner une erreur. [!DNL Marketo Measure] data
   * Si vous êtes un client Marketo Measure Ultimate et que vous avez défini votre objet de tableau de bord par défaut comme Contact, n’utilisez pas les deux champs ci-dessous spécifiques à la piste ([en savoir plus](/help/marketo-measure-ultimate/data-integrity-requirement.md){target="_blank"}).
      * b2b.personStatus
      * b2b.isConverted
* Notez que la section Étape d’opportunité est divisée en Perdu, Ouvert et Gagnant ; vérifiez que les étapes se trouvent dans la section d’étape appropriée.
   * Le fait qu’une étape se trouve dans une section d’étape incorrecte peut entraîner une erreur. [!DNL Marketo Measure] données sur les recettes ou les recettes de pipeline
* Évitez d’utiliser des noms d’étape en double (notre système les détectera et en supprimera automatiquement un).
* Pour définir une règle qui recherche des valeurs NULL, laissez la zone de texte Valeur vide.

## Bonnes pratiques relatives à la maintenance {#best-practices-for-maintenance}

La révision de votre mappage d’évaluation une fois par an vous permet de vous assurer que vos données d’opportunité dans [!DNL Marketo Measure] est exact et à jour.

Voici d’autres raisons pouvant déclencher une révision de votre mappage d’évaluation...

* Changements au sein de votre équipe marketing
* Toute modification apportée à vos étapes CRM
* Mises à jour de l’entonnoir de votre entreprise
* Affichage de données Recettes incorrectes dans votre [!DNL Marketo Measure] reporting

>[!MORELIKETHIS]
>
>[Différence entre les étapes d’entonnoir et les étapes de modèle personnalisées](/help/advanced-marketo-measure-features/custom-attribution-models/custom-attribution-model-and-setup.md#the-difference-between-funnel-stages-and-custom-model-stages)
