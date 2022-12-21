---
description: Bonnes pratiques pour la mise en oeuvre [!DNL Marketo Measure] JavaScript - [!DNL Marketo Measure] - Documentation du produit
title: Bonnes pratiques pour la mise en oeuvre [!DNL Marketo Measure] JavaScript
exl-id: 0359ad27-81e8-4902-a23a-49a5646a44d0
source-git-commit: cf144eb4bc9282ae6a260acd3735f24644292a19
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---

# Bonnes pratiques pour la mise en oeuvre [!DNL Marketo Measure] JavaScript {#best-practices-for-implementing-marketo-measure-javascript}

## APERÇU {#overview}

Le [!DNL Marketo Measure] JavaScript effectue le suivi des interactions marketing numérique de vos visiteurs web et est essentiel pour la variable [!DNL Marketo Measure] possibilité de créer des données de point de contact en ligne. La variable [!DNL Marketo Measure] Le code JavaScript déployé correctement et de manière globale sur l’ensemble de votre ou vos sites garantit que les données de session collectées produisent des données de point de contact précises.

Incohérences dans le déploiement de la variable [!DNL Marketo Measure] JavaScript entraîne des coupures dans les données de session, ce qui peut entraîner les éléments suivants :

* Attribution de canal/sous-canal incorrecte
* Perte de données source
* Niveaux élevés de trafic direct en erreur
* Rapports incohérents

[!DNL Marketo Measure] JavaScript est un élément fondamental de votre [!DNL Marketo Measure] compte et clé de votre succès !

## Bonne pratique {#best-practice}

Lorsqu’il s’agit de mettre en oeuvre et de gérer votre [!DNL Marketo Measure] Pour JavaScript, tenez compte des bonnes pratiques suivantes.

* Vérifiez que tous les domaines sont répertoriés dans votre [!DNL Marketo Measure] account
   * Si vous avez des questions concernant vos domaines, contactez l’assistance
* Déployez du code JavaScript sur TOUTES les pages.
   * Le placement de code JavaScript sur certaines pages uniquement entraîne des pauses dans les données de session, ce qui entraîne des erreurs. [!DNL Marketo Measure] data
* Pour un formulaire de votre site à partir duquel vous ne souhaitez pas créer de points de contact, veillez à ajouter la variable [!DNL Marketo Measure] Exclure le script
   * Ce script d’exclusions assure que la variable [!DNL Marketo Measure] les données de session ne seront pas perturbées et que les données source restent en place.
      * Voici quelques exemples de formulaires courants à supprimer :
         * Connexions des clients
         * Formulaires de mot de passe oubliés
         * Désabonner les formulaires
         * Formulaires de demande de carrière
* Examinez les sections &quot;Considérations supplémentaires&quot; et &quot;Forms pour accorder une plus grande attention à&quot; de la section Ajout de [!DNL Marketo Measure] Ressource de script répertoriée ci-dessous pour rechercher les scénarios qui peuvent nécessiter une gestion spéciale

## Bonne pratique pour la maintenance {#best-practice-for-maintenance}

Lors de la configuration de la variable [!DNL Marketo Measure] JavaScript est traité lors de la mise en oeuvre initiale. Les modifications apportées à votre site ou à l’équipe qui gère les modifications peuvent entraîner des interruptions de la [!DNL Marketo Measure] suivi. Nous vous recommandons de confirmer la variable [!DNL Marketo Measure] JavaScript est déployé correctement et intégralement une fois par an. En outre, si votre entreprise dispose d’une documentation sur le protocole de modification pour le site web, veillez à ce qu’une partie explique que [!DNL Marketo Measure] JavaScript doit être conservé/ajouté à toutes les nouvelles pages.

D’autres raisons peuvent déclencher une révision de votre configuration JavaScript, telles que...

* Chiffre d’affaires de votre équipe marketing
* Modifications et mises à jour de la structure de votre site
* Migration du site
* Modifications apportées à votre domaine
* Acquisition d’autres sociétés et de leurs propriétés web
