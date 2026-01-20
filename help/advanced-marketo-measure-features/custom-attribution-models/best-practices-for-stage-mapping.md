---
description: Bonnes pratiques relatives au mappage d’étape - [!DNL Marketo Measure]
title: Bonnes pratiques relatives au mappage des étapes
exl-id: 1ed380a1-4a3a-4761-b70f-cdf2e290329d
feature: Tracking, Custom Models
source-git-commit: 666812e8bf095170d611cd694b5d0ac5151d8fdd
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 4%

---

# Bonnes pratiques relatives au mappage des étapes {#best-practices-for-stage-mapping}

## Vue d’ensemble {#overview}

La section Mappage d’étape de votre compte [!DNL Marketo Measure] décrit les étapes que [!DNL Marketo Measure] extrait automatiquement de votre CRM et toutes les étapes personnalisées que vous avez définies à l’aide du modèle d’attribution personnalisé. La validité de vos données [!DNL Marketo Measure] repose sur le classement correct de ces étapes afin que [!DNL Marketo Measure] puissiez comprendre précisément votre funnel et la progression des enregistrements dans ladite funnel.

Dans la section Mappage d’étape de votre instance de [!DNL Marketo Measure], les étapes actives et inactives de votre CRM s’affichent. Classez toutes les étapes au mieux de vos capacités, conformément à la façon dont votre funnel se présente aujourd’hui.

Les étapes Funnel sont une autre fonctionnalité gérée dans cette section. Elles vous permettent d’ajouter des étapes au funnel sans appliquer l’attribution. Les étapes funnel seront suivies en tant que points de contact et seront renseignées dans le champ Positions de point de contact de votre CRM. Ces étapes Funnel seront également représentées au sein de divers tableaux de parcours dans [!DNL Marketo Measure] Discover.

## Meilleures pratiques {#best-practices}

Que vous évaluiez votre mappage d’étape pour la première fois ou que vous examiniez simplement votre ordre funnel, il est important de garder à l’esprit les bonnes pratiques suivantes.

* L&#39;ordre, c&#39;est tout !
   * Compte tenu des extractions de [!DNL Marketo Measure] dans les étapes actives et inactives de votre CRM, vérifiez que toutes les étapes qui peuvent être utilisées sur un lead/contact ou une opportunité sont regroupées et classées en conséquence
* Lors de la définition d’une étape personnalisée, assurez-vous que le suivi de l’historique des champs est activé pour le ou les champs utilisés pour définir l’étape
* N’utilisez pas de champ de formule pour définir une étape personnalisée
   * Un champ booléen est la recommandation de bonne pratique
* Notez que la section Étape du lead ou du contact est divisée en Perte, Ouverture et Convertie ; vérifiez que les étapes se trouvent dans la section d’étape appropriée
   * Le fait d’avoir une étape dans la mauvaise section d’étape peut entraîner des données [!DNL Marketo Measure] très incorrectes
   * Si vous êtes un client Marketo Measure Ultimate et que vous avez défini votre objet de tableau de bord par défaut en tant que contact, n’utilisez pas les deux champs ci-dessous spécifiques au prospect ([en savoir plus](/help/marketo-measure-ultimate/data-integrity-requirement.md){target="_blank"}).
      * b2b.personStatus
      * b2b.isConverted
* Notez que la section Étape de l’opportunité est divisée en Perdue, Ouverte et Confirmée ; vérifiez que les étapes se trouvent dans la section d’étape appropriée
   * Le fait d’avoir une étape dans la mauvaise section d’étape peut entraîner des données de chiffre d’affaires [!DNL Marketo Measure] ou de pipeline très incorrectes
* Évitez d’utiliser des noms d’étape en double (notre système les détectera et en supprimera automatiquement un).
* Pour définir une règle qui vérifie les valeurs NULL, laissez la zone de texte Valeur vide.

## Bonnes pratiques de maintenance {#best-practices-for-maintenance}

En examinant votre mappage d’étape une fois par an, vous vous assurerez que vos données d’opportunité en [!DNL Marketo Measure] sont exactes et à jour.

Les autres raisons qui peuvent déclencher une révision de votre mappage d’évaluation sont les suivantes :

* Changements au sein de votre équipe marketing
* Toutes les modifications apportées à vos étapes CRM
* Mises à jour du funnel de votre organisation
* Affichage de données de chiffre d’affaires incorrectes dans vos rapports [!DNL Marketo Measure]

>[!MORELIKETHIS]
>
>[La différence entre les étapes Funnel et les étapes de modèle personnalisé](/help/advanced-marketo-measure-features/custom-attribution-models/custom-attribution-model-and-setup.md#the-difference-between-funnel-stages-and-custom-model-stages)
