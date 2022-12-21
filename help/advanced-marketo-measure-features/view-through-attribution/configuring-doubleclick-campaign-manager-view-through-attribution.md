---
unique-page-id: 18874781
description: Configuration de l’affichage double du Gestionnaire de campagnes via l’attribution - [!DNL Marketo Measure] - Documentation du produit
title: Configuration de l’affichage double du Gestionnaire de campagnes via l’attribution
exl-id: 2cc6c2cd-afb7-4052-b18b-9ad0bf16a9fa
source-git-commit: b59c79236d3e324e8c8b07c5a6d68bd8176fc8a9
workflow-type: tm+mt
source-wordcount: '322'
ht-degree: 0%

---

# Configuration de l’affichage double du Gestionnaire de campagnes via l’attribution {#configuring-doubleclick-campaign-manager-view-through-attribution}

## Mesure de l’attribution des vues {#measuring-view-through-attribution}

>[!NOTE]
>
>Si vous utilisez la variable [!DNL Marketo Measure] et intégration de DoubleClick Campaign Manager, une [Connexion API](/help/api-connections/utilizing-marketo-measures-api-connections/integrated-ad-platforms.md#how-to-connect-ad-platforms) nous pouvons donc télécharger les détails des campagnes et des créatifs pour résoudre les publicités.

Pour commencer à obtenir des informations plus granulaires à partir de la vue via le suivi avec Doubleclick Campaign Manager, notre pixel de suivi doit être configuré.

Veuillez [cliquez ici](/help/advanced-marketo-measure-features/view-through-attribution/marketo-measure-view-through-attribution-faq.md) pour plus d’informations sur la variable [!DNL Marketo Measure] Attribution d’affichage publicitaire .

[!DNL Marketo Measure] est considérée comme une balise de rétrolien, car il s’agit d’un appel tiers via la balise publicitaire DCM. Les balises ping ne fonctionnent pas avec les balises d’image, mais uniquement avec les balises iframe ou javascript. Selon le support DCM, cela n&#39;a pas changé récemment et a toujours été le cas. Les balises standard ont été abandonnées le 2 octobre 2017, mais n’affectent pas la capacité de [!DNL Marketo Measure] pour effectuer le suivi des impressions.

Si vous utilisez une hiérarchie Parent et Enfant dans DCM, notre balise doit être appliquée à tous les niveaux pour le suivi des impressions.

## Ajout de la balise d’image {#how-to-add-the-image-tag}

Vous allez ajouter la balise dans Doubleclick sous le paramètre Annonceur et vous allez créer une balise d’événement d’impression.

1. Ajoutez le code suivant comme pixel d’image 1x1.

`https://cdn.bizibly.com/i?v=%eadv!&a=%eaid!&c=%ecid!&s=%esid!&p=%epid!&m=%m&n=%n`

1. Une fois ajoutées, vérifiez que les délimiteurs sont mappés comme suit. Cette fonction doit être automatique une fois la balise appliquée :

   v = %epuisque! Développer l’identifiant publicitaire\
   a = %eaid! Développer l’ID de publicité\
   c = %ecid! Développer L’Identifiant Créatif\
   s = %esid! Développer l’ID de site\
   p = %epid! Développer L’Id De Placement\
   m = %m Macro de code de correspondance\
   n = %n Macro de nombre aléatoire

   ![](assets/1.png)

## FAQ {#faq}

**Q : La balise d’image est-elle sécurisée ?**

A : Oui. Il ne s’agit pas d’une balise JavaScript, mais d’une balise d’image.

**Q : De quelles autorisations l’utilisateur connecté a-t-il besoin ?**

A : trafic de données, reporting, userinfo.email

**Q : Combien de temps cela peut-il prendre pour importer des données de dépenses ?**

A : Jusqu’à 6 heures

**Q : Combien de temps faut-il pour importer des données publicitaires ?**

A : Jusqu’à 6 heures
