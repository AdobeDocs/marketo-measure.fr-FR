---
description: Bonnes pratiques pour le package  [!DNL Marketo Measure]  CRM - [!DNL Marketo Measure]
title: 'Bonnes pratiques pour les packages CRM de [!DNL Marketo Measure] '
exl-id: 97ce0ff3-8aa5-4789-9ee0-25d68c001def
feature: Salesforce
source-git-commit: 666812e8bf095170d611cd694b5d0ac5151d8fdd
workflow-type: tm+mt
source-wordcount: '398'
ht-degree: 7%

---

# Bonnes pratiques relatives [!DNL Marketo Measure] package CRM {#best-practices-for-marketo-measure-crm-package}

>[!NOTE]
>
>Des instructions spécifiant « [!DNL Marketo Measure] » peuvent s’afficher dans la documentation. Toutefois, votre gestion de la relation client (CRM) mentionne encore « Bizible ». Cette a été mise à jour et le changement d’image se répercutera bientôt sur votre CRM.

## Vue d’ensemble {#overview}

[!DNL Marketo Measure] s’intègre à la fois à [!DNL Salesforce] et à [!DNL Microsoft Dynamics], ce document se concentre sur les bonnes pratiques [!DNL Marketo Measure] pour les packages CRM conçus pour [!DNL Salesforce].

Lors de la mise en œuvre, les deux packages suivants auraient été installés dans votre instance [!DNL Salesforce].

Package de base : il s’agit du package de base qui inclut les objets et champs personnalisés. Il est recommandé de l’installer dans Production pour tous les utilisateurs.
Package d’extension de tableau de bord : il s’agit de notre package d’extension de tableau de bord, qui contient trois tableaux de bord préconfigurés. Nous vous recommandons d’installer dans Production pour tous les utilisateurs. Cette option est facultative, mais nous encourageons les clients à l’installer.

Ces packages permettent à vos utilisateurs [!DNL Marketo Measure] d’accéder facilement aux données de point de contact dans leur instance [!DNL Salesforce]. Il est essentiel de confirmer que ces packages sont correctement configurés pour vérifier que les mises en page, les jeux d’autorisations, les rapports et les tableaux de bord s’affichent comme prévu pour vos utilisateurs [!DNL Marketo Measure].

## Bonne pratique {#best-practice}

Lors de l’implémentation et de la gestion de votre package de [!DNL Marketo Measure] [!DNL Salesforce], gardez à l’esprit les bonnes pratiques suivantes.

* Vérifiez que chaque membre de l’équipe nécessaire a accès aux dossiers de rapports [!DNL Marketo Measure]. Il doit y avoir 1 à 3 dossiers [!DNL Marketo Measure] (ceux-ci sont expliqués ci-dessous). Pour ouvrir l’accès, la personne qui a installé les packages doit partager les dossiers de rapports avec les utilisateurs ou rôles appropriés.
   * **Rapports Buyer Touchpoint** - disponibles pour tous
   * Rapports marketing basés sur les comptes **[!DNL Marketo Measure]** - les rapports ne seront renseignés que pour les clients de niveau 2 et supérieur
   * **Tableaux de bord Buyer Touchpoint** - disponibles pour tous, bien que ce package soit facultatif.

## Bonne pratique de maintenance {#best-practice-for-maintenance}

Bien que la configuration de votre package CRM soit couverte lors de la mise en œuvre initiale, il est recommandé de vérifier la configuration de votre package CRM une fois par an. Cette révision confirme que toutes les mises en page sont correctement configurées et que tous les membres de l’équipe concernés ont accès aux rapports et tableaux de bord [!DNL Marketo Measure].

D&#39;autres raisons pourraient déclencher un examen...

* Ajout de nouveaux membres de l’équipe
* Mises à jour des mises en page de vos pages [!DNL Salesforce]
* Migration de [!DNL Salesforce] Classic vers Lighching
* Mises à niveau de votre contrat [!DNL Marketo Measure]
* Vérifiez que la version la plus récente du Package de points de contact de l&#39;acheteur est installée dans [!DNL Salesforce]

>[!NOTE]
>
>Lorsque vous désactivez Marketo Measure pour l’exportation de données vers Salesforce, aucune donnée existante n’est supprimée. Pour le supprimer, suivez les étapes décrites dans [cet article d’aide de Salesforce](https://help.salesforce.com/s/articleView?language=en_US&id=sf.c360_a_delete_data_stream_records.htm&type=5){target="_blank"}.

>[!MORELIKETHIS]
>
>* [Mettre à jour le package Buyer Touchpoint](/help/configuration-and-setup/marketo-measure-and-salesforce/marketo-measure-salesforce-package-installation-and-set-up.md)
>* [[!DNL Marketo Measure] Jeux d’autorisations](/help/configuration-and-setup/marketo-measure-and-salesforce/marketo-measure-permission-sets.md)
>* [Dossier Partage de rapports et de tableaux de bord](https://help.salesforce.com/s/articleView?language=en_US&id=analytics_share_folder.htm&type=0)
>* [Connexion de Marketo Measure à Salesforce](/help/configuration-and-setup/marketo-measure-and-salesforce/connect-marketo-measure-to-salesforce.md)
