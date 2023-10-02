---
description: Notes de mise à jour actuelles - [!DNL Marketo Measure] - Documentation du produit
title: Notes de mise à jour actuelles
exl-id: 64b8fce8-af7d-4991-b01e-3fcf375d14e7
feature: Release Notes
source-git-commit: 22f8cedf401a28444026d7b63384ce3cbabe0305
workflow-type: tm+mt
source-wordcount: '536'
ht-degree: 44%

---

# Notes de mise à jour : 2023 {#release-notes-2023}

Vous trouverez ci-dessous toutes les nouvelles fonctionnalités et fonctionnalités mises à jour pour nos versions 2023.

## Version du 4e trimestre {#q4-release}

<p>

**Refonte du tableau de bord de Discover**

Tous les utilisateurs de Marketo Measure verront nos tableaux de bord in-app reconçus, qui combinent une convivialité améliorée à une valeur ajoutée. Nous introduisons également de nouvelles mesures, telles que le &quot;retour sur investissement réalisé&quot;, qui prend en compte le délai type entre les investissements marketing et les achats dans les marchés d’accès B2B.

Le nouvel ensemble de tableaux de bord prédéfinis devrait être introduit par vagues, à partir de la première semaine d’octobre et se terminer avant la fin de l’année. Ces nouveaux tableaux de bord s’affichent automatiquement dans vos instances, avec des informations sur les produits et des liens vers la documentation.

* [Nouveau guide de tableau de bord Discover](/help/marketo-measure-discover-ui/dashboards/new-discover-dashboard-guide.md){target="_blank"}
* [Découvrir les bases d’un tableau de bord](/help/marketo-measure-discover-ui/dashboards/discover-dashboard-basics.md){target="_blank"}
* [Tableau de bord Aperçu des recettes](/help/marketo-measure-discover-ui/dashboards/revenue-overview-dashboard.md){target="_blank"}
* [Tableau de bord des recettes affectées](/help/marketo-measure-discover-ui/dashboards/attributed-revenue-dashboard.md){target="_blank"}
* [Tableau de bord du retour sur investissement](/help/marketo-measure-discover-ui/dashboards/roi-dashboard.md){target="_blank"}
* [Tableau de bord des passeports](/help/marketo-measure-discover-ui/dashboards/passport-dashboard.md){target="_blank"}

>[!NOTE]
>
>Bien que les tableaux de bord actuels soient obsolètes à la mi-janvier 2024, vous pouvez utiliser les deux versions jusqu’à ce moment, ce qui garantit une transition fluide.

### Dépréciations {#deprecations}

<p>

* **Champ &quot;custom_properties&quot;**

Dans notre entrepôt de données, le champ &quot;custom_properties&quot; sert de stockage pour les points de données supplémentaires non couverts par notre schéma fixe. Stockée au format JSON, l’utilisation de ce champ est limitée et son intégration aux requêtes SQL peut être compliquée, ce qui affecte les performances. Compte tenu de ces facteurs, nous avons décidé d&#39;abandonner ce domaine. Cette modification concernera principalement la couche de traitement de données dans notre stockage de table Azure et les données exportées vers notre entrepôt de données.

* **Package Dynamics**

   * Pour rester connecté à Dynamics, installez notre dernière version de package, v6.12. Anciennes versions `(<v6.12)` ne sera plus prise en charge. Cette mise à jour optimise la création d’enregistrements historiques afin de réduire l’utilisation du stockage.

   * La méthode obsolète d’OAuth avec un RefreshToken sera obsolète. Reportez-vous à [ce guide](/help/marketo-measure-and-dynamics/getting-started-with-marketo-measure-and-dynamics/oauth-with-azure-active-directory-for-dynamics-crm.md){target="_blank"} pour mettre à jour vos informations d’identification afin de respecter les bonnes pratiques de Microsoft concernant l’utilisation de ClientSecret.

### Que va-t-il se passer ? {#q4-whats-coming}

<p>

**Création de rapports personnalisés in-app**

Pour la première fois, les clients Marketo Measure pourront créer et enregistrer leurs propres rapports directement dans l’application. Cette mise à jour fera suite à la publication des tableaux de bord préconfigurés début 2024.

<br>

## Version du 2e trimestre {#q2-release}

<p>

* **Consolidation des packages Salesforce**

Nous fusionnons tous les packages Salesforce en un seul package complet, pour une meilleure expérience utilisateur et une utilisation simplifiée. Les packages V1, V2_EXT et Reporting seront abandonnés au trimestre prochain. Le nouveau package combine toutes les fonctionnalités précédentes, pour un suivi plus efficace et des informations plus approfondies sur les clients et les clientes.

Les personnes qui disposent déjà du package V2 doivent le mettre à jour vers la nouvelle version consolidée.

Nous avons ajouté deux nouveaux champs qui vous aideront à améliorer vos capacités de reporting :

* form_name : désormais disponible dans les objets BT/BAT, ce champ permet aux utilisateurs et utilisatrices de créer des rapports en fonction des noms de formulaire.
* user_touchpoint_id : ce champ permet aux utilisateurs et utilisatrices de créer des rapports avec des nombres de points de contact utilisateur uniques.

[Cet article](/help/configuration-and-setup/marketo-measure-and-salesforce/salesforce-package-consolidation.md){target="_blank"} comprend des guides sur la recréation de rapports et de tableaux de bord à partir des packages de création de rapports hérités.

* **Mises à jour des versions d’API Salesforce**

Toutes les versions d’API Salesforce des classes Apex, y compris la classe UserActivityContext, sont mises à jour vers les versions prises en charge. (31.0 à 57.0)

* **Nouvelle installation du package**

Le nouveau lien d’installation consolidé du package [peut être consulté ici](https://login.salesforce.com/packaging/installPackage.apexp?p0=04t1P000000VY6Z){target="_blank"}

### Que va-t-il se passer ? {#q2-whats-coming}

<p>

**Modifications du stockage des adresses IP**

Nous ne stockerons plus d’adresses IP dans notre système conformément aux considérations en matière de confidentialité. Nous continuerons à identifier et stocker l’emplacement géographique de l’adresse IP, mais le format changera (par exemple, États-Unis en US).
