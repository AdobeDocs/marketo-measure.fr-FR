---
unique-page-id: 18874781
description: Configuration de l’affichage double du Gestionnaire de campagnes via l’attribution - [!DNL Marketo Measure]
title: Configuration l’attribution de visionnage moyen dans le gestionnaire de campagnes Doubleclick
exl-id: 2cc6c2cd-afb7-4052-b18b-9ad0bf16a9fa
feature: Attribution
source-git-commit: 48962b999fdd16fe96d18708ec301e64a39bc76e
workflow-type: tm+mt
source-wordcount: '417'
ht-degree: 27%

---

# Configuration l’attribution de visionnage moyen dans le gestionnaire de campagnes Doubleclick {#configuring-doubleclick-campaign-manager-view-through-attribution}

## Mesure de l’attribution des vues {#measuring-view-through-attribution}

>[!IMPORTANT]
>
>En raison de problèmes de confidentialité, des cookies tiers sont en cours d’élimination. L’abandon des cookies tiers annoncé par Google Chrome au troisième trimestre 2024 marque effectivement la fin de cette forme de suivi. Par conséquent, Adobe abandonnera les fonctions Marketo Measure qui reposent sur des cookies tiers, en particulier le suivi inter-domaines et l’attribution après affichage (View-through), qui utilisent le cookie d’impression Google/DoubleClick. Aucune autre fonction de Marketo Measure ne sera affectée. L’utilisation des cookies propriétaires ne sera pas non plus affectée. Compte tenu du planning de Google, la date d’obsolescence attendue des deux fonctions ci-dessus est le 01/06/2024. Les données connexes collectées avant cette date restent disponibles pour les clientes et clients Adobe.

>[!NOTE]
>
>Si vous utilisez l’intégration [!DNL Marketo Measure] et [!DNL DoubleClick Campaign Manager], nous avons besoin d’une [connexion API](/help/api-connections/utilizing-marketo-measures-api-connections/integrated-ad-platforms.md#how-to-connect-ad-platforms) afin que nous puissions télécharger les détails des campagnes et des créatifs pour résoudre les publicités.

Pour commencer à obtenir des informations plus granulaires depuis la vue jusqu’au suivi avec [!DNL Doubleclick Campaign Manager], notre pixel de suivi doit être configuré.

Pour plus d’informations sur la fonctionnalité [!DNL Marketo Measure] d’attribution d’affichages publicitaires, reportez-vous à la [FAQ sur l’attribution d’affichages publicitaires Marketo Measure](/help/advanced-marketo-measure-features/view-through-attribution/marketo-measure-view-through-attribution-faq.md).

[!DNL Marketo Measure] est considéré comme une balise piggyback, car il s’agit d’un appel tiers via la balise publicitaire DCM. Les balises ping ne fonctionnent pas avec les balises d’image, mais uniquement avec les balises iframe ou javascript. Selon le support DCM, cela n&#39;a pas changé récemment et a toujours été le cas. Les balises standard ont été abandonnées le 2 octobre 2017, mais n’affectent pas la capacité de [!DNL Marketo Measure] à suivre les impressions.

Dans le cas où vous utilisez une hiérarchie Parent et Enfant dans DCM, notre balise doit être appliquée à tous les niveaux pour le suivi des impressions.

## Ajout de la balise d’image {#how-to-add-the-image-tag}

Ajoutez la balise dans Doubleclick sous le paramètre Advertiser et créez une balise d’événement d’impression.

1. Ajoutez le code suivant comme pixel d’image 1x1.

`https://cdn.bizibly.com/i?v=%eadv!&a=%eaid!&c=%ecid!&s=%esid!&p=%epid!&m=%m&n=%n`

1. Une fois ajoutées, vérifiez que les délimiteurs sont mappés comme suit. Cette fonction doit être automatique une fois la balise appliquée :

   v = %epuisque! [!DNL Expand] Id Annonceur\
   a = %eaid! Développer l’ID de publicité\
   c = %ecid! Développer L’Identifiant Créatif\
   s = %esid! Développer l’ID de site\
   p = %epid! Développer L’Id De Placement\
   m = %m Macro de code de correspondance\
   n = %n Macro de nombre aléatoire

   ![](assets/1.png)

## Questions fréquentes {#faq}

**Q : La balise d’image est-elle sécurisée ?**

R : Oui. Il ne s’agit pas d’une balise JavaScript, mais d’une balise image.

**Q : De quelles autorisations l’utilisateur connecté a-t-il besoin ?**

A : trafic de données, reporting, userinfo.email

**Q : Combien de temps faut-il pour importer des données de dépenses ?**

A : Jusqu’à 6 heures

**Q : Combien de temps faut-il pour importer des données de publicité ?**

A : Jusqu’à 6 heures
