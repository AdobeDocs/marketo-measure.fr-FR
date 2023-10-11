---
description: Notes de mise à jour actuelles - [!DNL Marketo Measure] - Documentation du produit
title: Notes de mise à jour actuelles
exl-id: e93ff03e-ea21-41f4-abb8-32313ee74c0c
feature: Release Notes
source-git-commit: dc4fda07004398207fb5067eb42ecd9e8ffe8624
workflow-type: ht
source-wordcount: '536'
ht-degree: 100%

---

# Notes de mise à jour : 2023 {#release-notes-2023}

Vous trouverez ci-dessous toutes les nouvelles fonctionnalités et fonctionnalités mises à jour pour nos versions 2023.

## Version du 4e trimestre {#q4-release}

<p>

**Refonte du tableau de bord de Discover**

Bientôt disponibles pour tous les utilisateurs et toutes les utilisatrices de Marketo Measure, les tableaux de bord in-app font peau neuve et offrent plus de convivialité et d’efficacité. Nous introduisons également de nouvelles mesures, telles que le « Retour sur investissement réalisé », qui prend en compte le délai type entre les investissements marketing et les achats dans les stratégies B2B clé-en-main.

Ces nouveaux tableaux de bord intégrés seront progressivement déployés à partir de la première semaine d’octobre jusqu’à la fin de l’année. Ils seront automatiquement déployés sur vos instances et afficheront des informations sur les produits et des liens vers la documentation.

* [Nouveau guide du tableau de bord Discover](/help/marketo-measure-discover-ui/dashboards/new-discover-dashboard-guide.md){target="_blank"}
* [Bases du tableau de bord Discover](/help/marketo-measure-discover-ui/dashboards/discover-dashboard-basics.md){target="_blank"}
* [Tableau de bord Vue d’ensemble des revenus](/help/marketo-measure-discover-ui/dashboards/revenue-overview-dashboard.md){target="_blank"}
* [Tableau de bord Revenus affectés](/help/marketo-measure-discover-ui/dashboards/attributed-revenue-dashboard.md){target="_blank"}
* [Tableau de bord Retour sur investissement](/help/marketo-measure-discover-ui/dashboards/roi-dashboard.md){target="_blank"}
* [Tableau de bord Passeport](/help/marketo-measure-discover-ui/dashboards/passport-dashboard.md){target="_blank"}

>[!NOTE]
>
>À la mi-janvier 2024, les tableaux de bord actuels deviendront obsolètes. Pour assurer une transition fluide, vous pouvez utiliser les deux versions jusqu’à cette date.

### Obsolescence {#deprecations}

<p>

* **Champ « custom_properties »**

Dans notre entrepôt de données, le champ « custom_properties » sert de stockage pour les points de données supplémentaires non couverts par notre schéma fixe. L’utilisation de ce champ, stocké au format JSON, est limitée et son intégration aux requêtes SQL peut s’avérer compliquée et nuire aux performances. Nous avons donc décidé de rendre ce champ obsolète. Ce changement aura une incidence sur la couche de traitement de données dans notre stockage Table Azure et les données exportées vers notre entrepôt de données.

* **Package Dynamics**

   * Pour rester connecté à Dynamics, installez notre dernière version de package (6.12). Les anciennes versions `(<v6.12)` ne seront plus prise en charge. Cette mise à jour optimise la création d’enregistrements historiques afin de réduire l’utilisation du stockage.

   * La méthode OAuth par jeton d’actualisation a fait son temps et devient obsolète. Consultez ce [ce guide](/help/marketo-measure-and-dynamics/getting-started-with-marketo-measure-and-dynamics/oauth-with-azure-active-directory-for-dynamics-crm.md){target="_blank"} pour mettre à jour vos informations d’identification afin de respecter les bonnes pratiques de Microsoft concernant l’utilisation de ClientSecret.

### Que va-t-il se passer ? {#q4-whats-coming}

<p>

**Création de rapports personnalisés in-app**

Pour la première fois, les clients et clientes Marketo Measure pourront créer et enregistrer leurs propres rapports directement dans l’application. Cette fonctionnalité sera déployée après la publication des tableaux de bord intégrés début 2024.

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
