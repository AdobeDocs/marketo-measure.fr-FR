---
description: Bonnes pratiques pour [!DNL Marketo Measure] Package CRM - [!DNL Marketo Measure] - Documentation du produit
title: Bonnes pratiques pour [!DNL Marketo Measure] Package CRM
exl-id: 97ce0ff3-8aa5-4789-9ee0-25d68c001def
source-git-commit: 00268f49ff6e5dfc105fa7ea21837375eae49647
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 0%

---

# Bonnes pratiques pour [!DNL Marketo Measure] Package CRM {#best-practices-for-marketo-measure-crm-package}

>[!NOTE]
>
>Vous pouvez voir des instructions spécifiant &quot;[!DNL Marketo Measure]&quot; dans notre documentation, mais consultez toujours &quot;Bizible&quot; dans votre CRM. Nous nous efforçons de mettre à jour cette version et la nouvelle image sera bientôt répercutée dans votre CRM.

## APERÇU {#overview}

[!DNL Marketo Measure] s’intègre avec les deux [!DNL Salesforce] et [!DNL Microsoft Dynamics], ce document se concentrera sur le [!DNL Marketo Measure] bonnes pratiques pour les packages CRM conçus pour [!DNL Salesforce].

Pendant l’implémentation, les deux packages suivants ont été installés dans votre [!DNL Salesforce] instance.

Package de base : Il s’agit de notre package de base qui comprend nos objets et champs personnalisés. Nous vous recommandons d’installer dans Production pour tous les utilisateurs.
Package d’extension de tableau de bord : Il s’agit de notre package d’extension de tableau de bord, qui contient 3 tableaux de bord prédéfinis. Nous vous recommandons d’installer dans Production pour tous les utilisateurs. Cette option est facultative, mais nous encourageons les clients à l’installer.

Ces modules permettent à [!DNL Marketo Measure] les utilisateurs d’ accéder facilement aux données de point de contact sur l’ensemble de leur [!DNL Salesforce] instance. Confirmer que ces packages sont correctement configurés sera la clé pour vérifier que les mises en page, les jeux d’autorisations, les rapports et les tableaux de bord sont présentés à vos [!DNL Marketo Measure] utilisateurs comme prévu.

## Bonne pratique {#best-practice}

Lorsqu’il s’agit de mettre en oeuvre et de gérer votre [!DNL Marketo Measure] [!DNL Salesforce] Effectuez un package, tenez compte des bonnes pratiques suivantes.

* Vérifiez que chaque membre de l’équipe a accès à la variable [!DNL Marketo Measure] dossiers de rapports. Il doit y avoir 1-3 [!DNL Marketo Measure] dossiers (ils sont expliqués ci-dessous). Pour ouvrir l’accès, la personne ayant installé le ou les packages doit partager les dossiers de rapports avec les utilisateurs ou les rôles appropriés.
   * **Rapports Points de contact d’achat** - disponible pour tous
   * **[!DNL Marketo Measure]Rapports marketing basés sur les comptes** - les rapports ne seront renseignés que sur les clients de niveau 2 et supérieur.
   * **Tableaux de bord des points de contact d’acheteurs** - disponible à tous, bien que ce kit soit facultatif.

## Bonne pratique pour la maintenance {#best-practice-for-maintenance}

Bien que la configuration de votre package CRM soit traitée lors de la mise en oeuvre initiale, nous vous recommandons de passer en revue la configuration de votre package CRM une fois par an. Cette révision confirme que toutes les mises en page sont configurées correctement et que tous les membres de l’équipe appropriés ont accès à [!DNL Marketo Measure] rapports et tableaux de bord.

D’autres raisons peuvent déclencher une révision...

* Ajout de nouveaux membres de l’équipe
* Mises à jour à votre sujet [!DNL Salesforce] dispositions de page
* Migration pour [!DNL Salesforce] Classic to Lighting
* Mises à niveau vers vos [!DNL Marketo Measure] contrat
* Vérifiez que la version la plus récente de notre module Points de contact d’achat est installée dans [!DNL Salesforce]

>[!NOTE]
>
>Lorsque vous désactivez Marketo Measure pour exporter des données vers Salesforce, aucune donnée existante n’est supprimée. Pour le supprimer, suivez les étapes de la section [cet article d’aide de Salesforce](https://help.salesforce.com/s/articleView?id=sf.c360_a_delete_data_stream_records.htm&amp;type=5){target="_blank"}.

>[!MORELIKETHIS]
>
>* [Mettre à jour le module point de contact de l’utilisateur](/help/configuration-and-setup/marketo-measure-and-salesforce/marketo-measure-salesforce-package-installation-and-set-up.md)
>* [[!DNL Marketo Measure] Jeux d’autorisations](/help/configuration-and-setup/marketo-measure-and-salesforce/marketo-measure-permission-sets.md)
>* [Partage de dossiers Rapports et tableaux de bord](https://help.salesforce.com/articleView?id=analytics_share_folder.htm&amp;type=0)
>* [Connexion de Marketo Measure à Salesforce](/help/configuration-and-setup/marketo-measure-and-salesforce/connect-marketo-measure-to-salesforce.md)

