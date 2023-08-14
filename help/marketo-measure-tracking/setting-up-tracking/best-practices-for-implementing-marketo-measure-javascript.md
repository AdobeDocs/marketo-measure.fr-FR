---
description: Bonnes pratiques pour la mise en œuvre du code JavaScript  [!DNL Marketo Measure]  -  [!DNL Marketo Measure]  - Documentation du produit
title: Bonnes pratiques pour la mise en œuvre du code JavaScript  [!DNL Marketo Measure]
exl-id: 0359ad27-81e8-4902-a23a-49a5646a44d0
feature: Tracking
source-git-commit: 8ac315e7c4110d14811e77ef0586bd663ea1f8ab
workflow-type: ht
source-wordcount: '375'
ht-degree: 100%

---

# Bonnes pratiques pour la mise en œuvre du code JavaScript [!DNL Marketo Measure] {#best-practices-for-implementing-marketo-measure-javascript}

## Vue d’ensemble {#overview}

Le code JavaScript [!DNL Marketo Measure] effectue le suivi des interactions de marketing numérique de vos visiteurs web et est essentiel pour la fonction [!DNL Marketo Measure] de création des données de point de contact en ligne. Si vous déployez le code JavaScript [!DNL Marketo Measure] correctement et de manière globale sur l’ensemble de votre ou vos sites, cela garantit que les données de session collectées produisent des données de point de contact précises.

Les incohérences dans le déploiement du code JavaScript [!DNL Marketo Measure] entraîne des interruptions dans les données de session, ce qui peut entraîner les éléments suivants :

* Attribution de canal/sous-canal incorrecte
* Perte des données source
* Niveaux élevés de trafic direct erroné
* Rapports incohérents

Le code JavaScript [!DNL Marketo Measure] est un élément fondamental de votre compte [!DNL Marketo Measure] et constitue la clé de votre succès !

## Bonne pratique {#best-practice}

Lorsqu’il s’agit de mettre en œuvre et de gérer votre code JavaScript [!DNL Marketo Measure], tenez compte des bonnes pratiques suivantes.

* Vérifiez que tous les domaines sont répertoriés dans votre compte [!DNL Marketo Measure]
   * Si vous avez des questions concernant vos domaines, contactez l’assistance
* Déployez du code JavaScript sur TOUTES les pages.
   * Le placement de code JavaScript sur certaines pages uniquement entraîne des interruptions dans les données de session, ce qui entraîne des données [!DNL Marketo Measure] incorrectes
* Pour un formulaire sur votre site à partir duquel vous ne souhaitez pas créer de points de contact, veillez à ajouter le script d’exclusions [!DNL Marketo Measure]
   * Ce script d’exclusions garantit que les données de session [!DNL Marketo Measure] ne seront pas perturbées et que les données source restent en place
      * Voici quelques exemples de formulaires courants à supprimer :
         * Connexions des clients/clientes
         * Formulaires de mot de passe oublié
         * Formulaires de désinscription
         * Formulaires de candidature à un poste
* Consultez les sections « Considérations supplémentaires » et « Formulaires auxquels prêter une attention particulière » de la ressource Ajout d’un script [!DNL Marketo Measure] répertoriée ci-dessous pour rechercher les scénarios qui peuvent nécessiter une gestion spéciale

## Bonne pratique de maintenance {#best-practice-for-maintenance}

Bien que la configuration du code JavaScript [!DNL Marketo Measure] soit traitée lors de la mise en œuvre initiale, les modifications apportées à votre site ou à l’équipe qui gère les modifications peuvent entraîner des interruptions du suivi de [!DNL Marketo Measure]. Nous vous recommandons de vérifier que le code JavaScript [!DNL Marketo Measure] est déployé correctement et intégralement une fois par an. En outre, si votre entreprise dispose d’une documentation sur le protocole de modification pour le site web, veillez à ce qu’une partie explique que le code JavaScript [!DNL Marketo Measure] doit être conservé/ajouté à toutes les nouvelles pages.

Il existe d’autres raisons qui peuvent déclencher une révision de la configuration de votre code JavaScript, notamment...

* Changements au sein de votre équipe marketing
* Modifications et mises à jour de la structure de votre site
* Migrations du site
* Modifications apportées à votre domaine
* Acquisition d’autres entreprises et de leurs propriétés web
