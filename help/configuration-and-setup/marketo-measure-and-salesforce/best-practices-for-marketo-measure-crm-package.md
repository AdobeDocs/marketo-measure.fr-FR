---
description: Bonnes pratiques pour le  [!DNL Marketo Measure] package CRM - [!DNL Marketo Measure]
title: Bonnes pratiques pour les packages CRM de [!DNL Marketo Measure]
exl-id: 97ce0ff3-8aa5-4789-9ee0-25d68c001def
feature: Salesforce
source-git-commit: 915e9c5a968ffd9de713b4308cadb91768613fc5
workflow-type: tm+mt
source-wordcount: '398'
ht-degree: 7%

---

# Bonnes pratiques pour le package CRM [!DNL Marketo Measure] {#best-practices-for-marketo-measure-crm-package}

>[!NOTE]
>
>Des instructions spécifiant « [!DNL Marketo Measure] » peuvent s’afficher dans la documentation. Toutefois, votre gestion de la relation client (CRM) mentionne encore « Bizible ». Il est mis à jour et le changement de marque sera bientôt répercuté dans votre CRM.

## Vue d’ensemble {#overview}

[!DNL Marketo Measure] s&#39;intègre à la fois à [!DNL Salesforce] et à [!DNL Microsoft Dynamics]. Ce document se concentre sur les [!DNL Marketo Measure] bonnes pratiques pour les packages CRM conçus pour [!DNL Salesforce].

Pendant la mise en oeuvre, les deux packages suivants auraient été installés dans votre instance [!DNL Salesforce].

Package de base : il s’agit du package de base qui inclut des objets et des champs personnalisés. Il est recommandé de l’installer dans Production pour tous les utilisateurs.
Package d’extension de tableau de bord : il s’agit de notre package d’extension de tableau de bord, qui contient trois tableaux de bord prédéfinis. Nous vous recommandons d’installer dans Production pour tous les utilisateurs. Cette option est facultative, mais nous encourageons les clients à l’installer.

Ces packages permettent à vos utilisateurs [!DNL Marketo Measure] d’accéder facilement aux données de point de contact sur leur instance [!DNL Salesforce]. Confirmer que ces packages sont correctement configurés est la clé pour vérifier que les mises en page, les jeux d’autorisations, les rapports et les tableaux de bord sont présentés à vos utilisateurs [!DNL Marketo Measure] comme prévu.

## Bonne pratique {#best-practice}

Lors de l&#39;implémentation et de la gestion de votre package [!DNL Marketo Measure] [!DNL Salesforce], gardez à l&#39;esprit les bonnes pratiques suivantes.

* Vérifiez que chaque membre de l’équipe nécessaire a accès aux dossiers de rapports [!DNL Marketo Measure]. Il doit y avoir 1 à 3 dossiers [!DNL Marketo Measure] (ceux-ci sont expliqués ci-dessous). Pour ouvrir l’accès, la personne qui a installé les packages doit partager les dossiers des rapports avec les utilisateurs ou les rôles appropriés.
   * **Rapports Buyer Touchpoint** - disponibles pour tous
   * **[!DNL Marketo Measure]Rapports marketing basés sur les comptes** : les rapports ne seront renseignés que pour les clients de niveau 2 et supérieur.
   * **Tableaux de bord Buyer Touchpoint** - disponibles à tous, bien que ce module soit facultatif.

## Bonne pratique de maintenance {#best-practice-for-maintenance}

Bien que la configuration de votre package CRM soit traitée lors de la mise en oeuvre initiale, il est recommandé de passer en revue la configuration de votre package CRM une fois par an. Cette révision confirme que toutes les mises en page sont configurées correctement et que tous les membres de l’équipe appropriés ont accès aux rapports et aux tableaux de bord [!DNL Marketo Measure].

D’autres raisons peuvent déclencher une révision...

* Ajout de nouveaux membres de l’équipe
* Mises à jour des mises en page [!DNL Salesforce]
* Migration de [!DNL Salesforce] Classic vers Lightening
* Mises à niveau de votre contrat [!DNL Marketo Measure]
* Vérifiez que la version la plus récente du module Points de contact de l’acheteur est installée dans [!DNL Salesforce].

>[!NOTE]
>
>Lorsque vous désactivez Marketo Measure pour exporter des données vers Salesforce, aucune donnée existante n’est supprimée. Pour le supprimer, suivez les étapes de [cet article d’aide Salesforce](https://help.salesforce.com/s/articleView?language=en_US&amp;id=sf.c360_a_delete_data_stream_records.htm&amp;type=5){target="_blank"}.

>[!MORELIKETHIS]
>
>* [Mettre à jour le package Buyer Touchpoint](/help/configuration-and-setup/marketo-measure-and-salesforce/marketo-measure-salesforce-package-installation-and-set-up.md)
>* [[!DNL Marketo Measure] Jeux d’autorisations](/help/configuration-and-setup/marketo-measure-and-salesforce/marketo-measure-permission-sets.md)
>* [Partage de dossiers Rapports et tableaux de bord](https://help.salesforce.com/s/articleView?language=en_US&amp;id=analytics_share_folder.htm&amp;type=0)
>* [Connecter Marketo Measure à Salesforce](/help/configuration-and-setup/marketo-measure-and-salesforce/connect-marketo-measure-to-salesforce.md)
