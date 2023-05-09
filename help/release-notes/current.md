---
description: Notes de mise à jour actuelles - [!DNL Marketo Measure] - Documentation du produit
title: Notes de mise à jour actuelles
source-git-commit: 8e8ddd80d69102455fa678a32f31a9fe8319822c
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 0%

---

# Notes de mise à jour : 2023 {#release-notes-2023}

Vous trouverez ci-dessous toutes les nouvelles fonctionnalités et fonctionnalités mises à jour pour nos versions 2023.

## Version du 2e trimestre {#q2-release}

<p>

**Consolidation des modules Salesforce**

* Nous fusionnons tous les modules Salesforce en un seul module complet pour une meilleure expérience utilisateur et une utilisation simplifiée. Les modules V1, V2_EXT et Reporting seront abandonnés au trimestre prochain. Le nouveau package combine toutes les fonctionnalités précédentes, ce qui permet un suivi plus efficace et des informations plus approfondies sur les clients.
* Les clients qui disposent déjà du package V2 doivent le mettre à jour vers la nouvelle version consolidée.
* Nous avons ajouté deux nouveaux champs pour améliorer vos capacités de reporting :
   * form_name: Désormais disponible dans les objets BT/BAT, ce champ permet aux utilisateurs de créer des rapports en fonction des noms de formulaire.
   * user_touchpoint_id: Ce champ permet aux utilisateurs de créer des rapports avec des nombres de points de contact utilisateur uniques.
* [Cet article](/help/configuration-and-setup/marketo-measure-and-salesforce/salesforce-package-consolidation.md){target="_blank"} comprend des guides sur la recréation de rapports et de tableaux de bord à partir des packages de création de rapports hérités.

**Mises à jour de la version de l’API Salesforce**

* Toutes les versions d’API Salesforce des classes Apex, y compris la classe UserActivityContext, sont mises à jour vers les versions prises en charge. (31.0 à 57.0)

**Nouvelle installation du package**

* Le nouveau lien d’installation consolidé du package [peut être consulté ici](https://login.salesforce.com/packaging/installPackage.apexp?p0=04t1P000000VY6Z){target="_blank"}

### Que vient-il ? {#whats-coming}

<p>

**Modifications du stockage des adresses IP**

* Nous ne stockerons plus d’adresses IP dans notre système en fonction des considérations de confidentialité. Nous continuerons à identifier et stocker l’emplacement géographique de l’adresse IP, mais le format changera (par exemple, &quot;États-Unis&quot; en &quot;États-Unis&quot;).
