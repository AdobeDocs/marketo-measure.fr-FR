---
description: Configuration De La Vue DoubleClick Campaign Manager Via L’Attribution - [!DNL Marketo Measure]
title: Configuration l’attribution de visionnage moyen dans le gestionnaire de campagnes Doubleclick
exl-id: 2cc6c2cd-afb7-4052-b18b-9ad0bf16a9fa
feature: Attribution
source-git-commit: c6090ce0c3ac60cd68b1057c369ce0b3b20aeeee
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 26%

---


# Configuration l’attribution de visionnage moyen dans le gestionnaire de campagnes Doubleclick {#configuring-doubleclick-campaign-manager-view-through-attribution}

## Mesure de la vue via l’attribution {#measuring-view-through-attribution}

>[!IMPORTANT]
>En raison de problèmes de confidentialité, des cookies tiers sont en cours d’élimination. L’abandon des cookies tiers annoncé par Google Chrome au troisième trimestre 2024 marque effectivement la fin de cette forme de suivi. Par conséquent, Adobe abandonnera les fonctions Marketo Measure qui reposent sur des cookies tiers, en particulier le suivi inter-domaines et l’attribution après affichage (View-through), qui utilisent le cookie d’impression Google/DoubleClick. Aucune autre fonction de Marketo Measure ne sera affectée. L’utilisation des cookies propriétaires ne sera pas non plus affectée. Compte tenu du planning de Google, la date d’obsolescence attendue des deux fonctions ci-dessus est le 01/06/2024. Les données connexes collectées avant cette date restent disponibles pour les clientes et clients Adobe.

>[!NOTE]
>Si vous utilisez l’intégration [!DNL Marketo Measure] et [!DNL DoubleClick Campaign Manager], nous avons besoin d’une connexion [API](/help/api-connections/integrated-ad-platforms.md#how-to-connect-ad-platforms) afin de pouvoir télécharger les détails des campagnes et des contenus publicitaires pour résoudre les annonces.

Pour commencer à obtenir plus d’insight granulaire à partir de la vue via le suivi avec [!DNL Doubleclick Campaign Manager], notre pixel de suivi doit être configuré.

Pour plus d’informations sur la fonctionnalité [!DNL Marketo Measure] Afficher via l’attribution, consultez la [FAQ sur l’affichage via l’attribution de Marketo Measure](/help/advanced-features/view-through-attribution/marketo-measure-view-through-attribution-faq.md).

[!DNL Marketo Measure] est considéré comme une balise de rattachement, car il s’agit d’un appel tiers via la balise publicitaire DCM. Les balises de récupération ne fonctionnent pas avec les balises d’image, mais uniquement avec les balises iframe ou JavaScript. Selon le support DCM, cela n’a pas changé récemment et a toujours été le cas. Les balises standard ont été abandonnées le 2 octobre 2017, mais n’affectent pas la capacité de [!DNL Marketo Measure] à effectuer le suivi des impressions.

Si vous utilisez une hiérarchie Parent et Enfant dans DCM, notre balise devra être appliquée à tous les niveaux pour le suivi des impressions.

## Comment ajouter la balise d’image {#how-to-add-the-image-tag}

Ajoutez la balise dans Doubleclick sous le paramètre Publicitaire et créez une balise d’événement d’impression.

1. Ajoutez le code suivant en tant que pixel d’image 1x1.

`https://cdn.bizibly.com/i?v=%eadv!&a=%eaid!&c=%ecid!&s=%esid!&p=%epid!&m=%m&n=%n`

1. Une fois ajouté, vérifiez que les délimiteurs sont mappés comme suit. Cette opération doit être automatique une fois la balise appliquée :

   v = %eadv! ID publicitaire [!DNL Expand]\
   a = %eaid! Développer l’ID de publicité\
   c = %ecid! Développer l’ID Creative\
   s = %esid! Développer l’ID du site\
   p = %epid! Développer l’ID d’emplacement\
   m = %m Macro de code de correspondance\
   n = %n Macro à nombres aléatoires

   ![Balise DCM Floodlight configurée avec des macros Marketo Measure](assets/1.png)

## Questions fréquentes {#faq}

**Q : La balise d’image est-elle sécurisée ?**

R : Oui. Il ne s’agit pas d’une balise JavaScript, mais d’une balise image.

**Q : De quelles autorisations l’utilisateur connecté a-t-il besoin ?**

A : dfatraffic, dfareporting, userinfo.email

**Q : Combien de temps faut-il pour importer les données de dépenses ?**

A : Jusqu’à 6 heures

**Q : Combien de temps faut-il pour importer les données publicitaires ?**

A : Jusqu’à 6 heures
