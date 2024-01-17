---
description: « Guide de mise en œuvre [!DNL Marketo Measure] Ultimate –  [!DNL Marketo Measure]  – Documentation du produit »
title: Guide de mise en œuvre [!DNL Marketo Measure] Ultimate
feature: Integration, Tracking, Attribution
source-git-commit: 7bb458941e513b6155b834d27f76f0b5df4e0a09
workflow-type: tm+mt
source-wordcount: '997'
ht-degree: 97%

---

# Guide de mise en œuvre [!DNL Marketo Measure] Ultimate {#marketo-measure-ultimate-implementation-guide}

Cet article sert de guide de mise en œuvre de Marketo Measure Ultimate. Il fournit des instructions et des informations claires garantissant une intégration et une utilisation réussies.

## Principales différences lors de l’utilisation de l’option Ultimate par rapport aux niveaux standard {#main-differences-when-using-ultimate-over-standard-tiers}

Importer des données B2B via AEP : les personnes spécialisées dans le marketing peuvent importer leurs données B2B (par exemple, compte, opportunité, contact, lead, campagne, personne membre de campagne, activité) via AEP. Ingérez des données de presque toutes les sources de données, ainsi que de plusieurs sources de données du même type, afin d’importer toutes vos données pour l’attribution.

* Utilisez-le avec presque tous les CRM, pas uniquement Salesforce et Dynamics.
* Connectez plusieurs instances CRM et/ou MAP à une instance Marketo Measure.
* Incluez des données d’inscription et de participation à des webinaires tiers.

Les connexions directes au CRM et à Marketo Engage ne sont plus disponibles pour Ultimate.

* Ultimate ne repousse pas les données vers le CRM. La clientèle peut utiliser les données de l’entrepôt de données.
* Les personnes spécialisées dans le marketing continueront à importer les données de la plateforme d’annonces publicitaires par le biais de connexions directes et à effectuer le suivi des activités web par le biais du code JavaScript Marketo Measure.

Les personnes utilisant Ultimate sont approvisionnées par AEP. Si elles disposent déjà d’AEP, aucune nouvelle instance n’est réapprovisionnée.

* La version AEP configurée comprend tous les connecteurs source, la modélisation des données de schéma, les jeux de données, le service de requête ad hoc et une destination pour Marketo Measure uniquement.

En savoir plus sur [Marketo Measure Ultimate](/help/marketo-measure-ultimate/marketo-measure-ultimate-overview.md){target="_blank"}.

## Schémas et jeux de données {#schemas-and-datasets}

>[!NOTE]
>
>Consultez [Blocs de création d’un schéma](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/composition.html?lang=fr#building-blocks-of-a-schema){target="_blank"} pour avoir une vue d’ensemble des schémas, des classes et des groupes de champs.

**Schéma XDM = Classe + Groupe de champs de schéma&#42;**

* Les champs obligatoires ne sont pas modifiables. La clientèle peut créer et ajouter des champs personnalisés selon ses attentes.
* Exemple de nom de champ basé sur la hiérarchie : accountOrganization.annualRevenue.amount

&#42; _Un schéma comprend une classe et zéro ou plus de zéro groupes de champs de schéma. Cela signifie que vous pouvez composer un schéma de jeu de données sans utiliser de groupes de champs._

![](assets/marketo-measure-ultimate-implementation-guide-1.png)

[Vue d’ensemble des jeux de données](https://experienceleague.adobe.com/docs/experience-platform/catalog/datasets/overview.html?lang=fr){target="_blank"} : toutes les données correctement ingérées dans AEP sont conservées en tant que jeux de données dans le lac de données. Un jeu de données est une structure de stockage et de gestion pour une collecte de données, généralement sous la forme de tableau, qui contient un schéma (des colonnes) et des champs (des lignes).

## Créer un schéma {#creating-a-schema}

Nous vous recommandons d’utiliser un utilitaire de génération automatique pour créer 10 schémas B2B standard.

* Les étapes de téléchargement et de configuration de l’utilitaire [peuvent être consultées ici](https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo-namespaces.html?lang=fr#set-up-b2b-namespaces-and-schema-auto-generation-utility){target="_blank"}.

Pour les personnes qui disposent d’un _**Droit CDP**_ : créez des schémas en accédant à la page Sources.

* Depuis une source, sélectionnez Ajouter des données > Utiliser des modèles.

![](assets/marketo-measure-ultimate-implementation-guide-2.png)

* Sélectionnez un compte et tous les modèles B2B pour créer 10 schémas B2B standard.

![](assets/marketo-measure-ultimate-implementation-guide-3.png)

## Flux de données {#dataflows}

[Vue d’ensemble des flux de données](https://experienceleague.adobe.com/docs/experience-platform/dataflows/home.html?lang=fr){target="_blank"}

**Étapes de création d’un flux de données :**

1. Sélectionnez une source.
1. Sélectionnez un compte existant ou créez-en un.
1. Sélectionnez un type de données dans la liste des types disponibles à l’import à partir de la source.
1. Sélectionnez le jeu de données existant ou créez-en un.
1. Mappez les champs de la source au schéma.

   >[!NOTE]
   >
   >* Si vous mappez un type de schéma à un autre type identique, l’opération est automatique.
   >* Vous pouvez également importer le mappage à partir d’un autre flux du système.
   >* Vous pouvez mapper un champ Source à plusieurs champs de destination, mais le contraire est impossible.
   >* Vous pouvez créer des champs calculés ([fonctions de mappage de la préparation de données](https://experienceleague.adobe.com/docs/experience-platform/data-prep/functions.html?lang=fr){target="_blank"}).

   >[!CAUTION]
   >
   >* Vous pouvez modifier un flux de données, mais les données ne sont pas renvoyées lorsqu’un mappage est modifié.
   >* Si un champ obligatoire est NULL, l’ensemble du flux est rejeté.

   >[!NOTE]
   >
   >[Exigence d’intégrité des données de Marketo Measure Ultimate](/help/marketo-measure-ultimate/data-integrity-requirement.md){target="_blank"}

1. Définissez une cadence de chargement des données.
1. Vérifiez et validez.
1. Consultez la page « Statut du compte » dans les paramètres de l’interface utilisateur de Measure pour connaître le statut du flux de données.

**Surveillance :**

Page Sources > Flux de données pour vérifier le statut des flux de données

* Pour afficher les détails de l’activité d’un jeu de données, cliquez simplement sur le jeu de données.
* Pour afficher les erreurs de flux de données, sélectionnez un flux de données, choisissez une exécution de flux de données, puis cliquez sur « Vue d’ensemble des diagnostics d’erreur ».

## Inspection des données {#data-inspection}

Option 1 : pour exécuter des requêtes directement à partir de l’interface utilisateur, accédez à l’onglet Requêtes sous Gestion des données.

![](assets/marketo-measure-ultimate-implementation-guide-4.png)

Option 2 : [téléchargez et utilisez PSQL](https://experienceleague.adobe.com/docs/experience-platform/query/clients/psql.html?lang=fr){target="_blank"} (plus rapide et plus fiable).

## Activer le jeu de données pour Marketo Measure {#activate-dataset-for-marketo-measure}

Avant de commencer, accédez à la section « Experience Platform > Mappage des sandbox » dans les paramètres de l’interface utilisateur de Measure et mappez un sandbox.

>[!CAUTION]
>
>Ce choix ne peut pas être modifié une fois sélectionné.

1. Dans AEP, accédez à « Destinations > page Marketo Measure » pour exporter des jeux de données.
1. Configurez la destination.
1. Activez le jeu de données.
1. Consultez la page « Statut du compte » dans les paramètres de l’interface utilisateur de Measure pour connaître le statut du flux de données.

>[!NOTE]
>
>* Les données d’une entité donnée (un compte, par exemple) provenant d’une source de données particulière ne peuvent entrer que dans un seul jeu de données. Chaque jeu de données ne peut être inclus que dans un seul flux de données. Les violations arrêtent le flux de données au moment de l’exécution.
>* Supprimez la destination entière dans AEP pour supprimer les données dans Measure. La désactivation ne fera qu’arrêter les nouveaux exports de données et les anciennes données seront conservées.
>* La configuration de Measure sera pour la plupart identique, mais certaines parties, comme le mappage des étapes, auront un aspect différent.
>* Quelques heures sont nécessaires pour qu’un nouveau flux de données génère une exécution de flux, ces dernières se produisant à intervalles horaires réguliers.

Dans Measure, la devise par défaut doit être définie dans la section « Devise ».

* Si vous utilisez plusieurs devises, le schéma de taux de conversion de devise doit être renseigné dans AEP pour qu’il puisse être lu et utilisé pour les conversions.

**Mappage d’étape :**

Les étapes n’étant pas automatiquement importées à partir des données de l’utilisateur ou de l’utilisatrice, elles doivent être mappées manuellement.

* Les utilisateurs et utilisatrices peuvent mapper des étapes à partir de différentes sources.

![](assets/marketo-measure-ultimate-implementation-guide-5.png)

Si les étapes ne sont pas mappées, le système ne fonctionnera pas, car les données ne pourront aller nulle part.

Si vous êtes un client Marketo Measure Ultimate et que vous avez défini votre objet de tableau de bord par défaut comme Contact, n’utilisez pas les deux champs ci-dessous spécifiques à la piste ([en savoir plus ici](/help/marketo-measure-ultimate/data-integrity-requirement.md){target="_blank"}).

* b2b.personStatus
* b2b.isConverted

**Règles des personnes membres de la campagne**

Vous devez sélectionner un jeu de données et définir des règles pour chacun d’eux.

**Règles des événements d’expérience**

Vous devez sélectionner un jeu de données et les types d’activité.

* Les activités personnalisées ne sont pas prises en charge.
* Si la clientèle a des activités qui ne correspondent pas aux options disponibles, nous vous suggérons de les classer comme « Moments intéressants » et d’utiliser des champs personnalisés pour les distinguer.

**Canaux hors ligne :**

* Nous ne créons pas de règles de mappage de canal spécifiques à un jeu de données, pour une approche globale.
* Nous devons éventuellement faire correspondre le type de campagne CRM et le canal, mais pour l’instant, nous pouvons mapper le nom du canal aux deux champs comme solution de contournement.
* **Règles de canal : les données renvoyées ne comportent pas de données de transition d’étapes.**

Les paramètres Touchpoint et Segment restent les mêmes.
