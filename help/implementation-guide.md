---
description: « [!DNL Marketo Measure] Guide de mise en œuvre d’Ultimate - [!DNL Marketo Measure] »
title: Guide de mise en œuvre [!DNL Marketo Measure] Ultimate
feature: Integration, Tracking, Attribution
exl-id: 0c707875-5d05-49b9-b1ff-c3f7b711ebd1
source-git-commit: fcd8e276c85669ddf12bd7404fb12d3e99b2642a
workflow-type: tm+mt
source-wordcount: '1059'
ht-degree: 60%

---

# Guide de mise en œuvre [!DNL Marketo Measure] Ultimate {#marketo-measure-ultimate-implementation-guide}

Cet article sert de guide de mise en œuvre de Marketo Measure Ultimate. Il fournit des instructions et des informations claires garantissant une intégration et une utilisation réussies.

## Principales différences lors de l’utilisation de l’option Ultimate par rapport aux niveaux standard {#main-differences-when-using-ultimate-over-standard-tiers}

Importer des données B2B via AEP : les marketeurs sont censés importer leurs données B2B (par exemple, compte, opportunité, contact, lead, campagne, membre de campagne, activité) via AEP. Ingérez des données de presque toutes les sources de données, ainsi que de plusieurs sources de données du même type, afin d’importer toutes vos données pour l’attribution.

* Utilisez-le avec presque tous les CRM, pas uniquement Salesforce et Dynamics.
* Connectez plusieurs instances CRM et/ou MAP à une instance Marketo Measure.
* Incluez des données d’inscription et de participation à des webinaires tiers.

Les connexions directes au CRM et à Marketo Engage ne sont plus disponibles pour Ultimate.

* Ultimate ne repousse pas les données vers le CRM. La clientèle peut utiliser les données de l’entrepôt de données.
* Les marketeurs continuent d’importer les données d’Ad Platform par le biais de connexions directes et du suivi des activités web via Marketo Measure JavaScript.

Les utilisateurs d’Ultimate sont configurés pour AEP. S’ils disposent déjà d’AEP, nous ne reconfigurerons pas une nouvelle instance.

* La version d’AEP configurée inclut tous les connecteurs source, la modélisation des données de schéma, les jeux de données, le service de requête ad hoc et une destination pour Marketo Measure uniquement.

En savoir plus sur [Marketo Measure Ultimate](/help/migration-from-tier-to-marketo-measure-ultimate.md){target="_blank"}.

## Schémas et jeux de données {#schemas-and-datasets}

>[!NOTE]
>
>Consultez la section [Création de blocs d’un schéma](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/composition.html?lang=fr#building-blocks-of-a-schema){target="_blank"} pour obtenir un aperçu des schémas, des classes et des groupes de champs.

**Schéma XDM = Classe + Groupe de champs de schéma&#42;**

* Les champs obligatoires ne sont pas modifiables. La clientèle peut créer et ajouter des champs personnalisés selon ses attentes.
* Exemple de nom de champ basé sur la hiérarchie : accountOrganization.annualRevenue.amount

&#42; _Un schéma comprend une classe et zéro ou plus de zéro groupes de champs de schéma. Cela signifie que vous pouvez composer un schéma de jeu de données sans utiliser de groupes de champs._

![&42; Un schéma comprend une classe et zéro ou plusieurs champs de schéma](assets/marketo-guide-1.png)

[Présentation des jeux de données](https://experienceleague.adobe.com/en/docs/experience-platform/catalog/datasets/overview#){target="_blank"} : toutes les données correctement ingérées par AEP sont conservées sous forme de jeux de données dans le lac de données. Un jeu de données est une structure de stockage et de gestion pour une collecte de données, généralement sous la forme de tableau, qui contient un schéma (des colonnes) et des champs (des lignes).

## Créer un schéma {#creating-a-schema}

Nous vous recommandons d’utiliser un utilitaire de génération automatique pour créer dix schémas B2B standard.

* Les étapes de téléchargement et de configuration de l’utilitaire [se trouvent ici](https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo-namespaces.html?lang=fr#set-up-b2b-namespaces-and-schema-auto-generation-utility){target="_blank"}.

Pour les personnes qui disposent d’un _&#x200B;**Droit CDP**&#x200B;_ : créez des schémas en accédant à la page Sources.

* Depuis une source, sélectionnez Ajouter des données > Utiliser des modèles.

![Dans une source, sélectionnez Ajouter des modèles d’utilisation des données](assets/marketo-guide-2.png)

* Sélectionnez un compte et tous les modèles B2B pour créer dix schémas B2B standard.

![Sélectionnez un compte et tous les modèles B2B pour créer dix modèles B2B standard](assets/marketo-guide-3.png)

## Flux de données {#dataflows}

>[!IMPORTANT]
>
>Lors de l’ajout d’un nouveau jeu de données, nous vous recommandons de créer un flux au lieu d’utiliser un flux existant.

[Présentation des flux de données](https://experienceleague.adobe.com/docs/experience-platform/dataflows/home.html?lang=fr){target="_blank"}

**Étapes de création d’un flux de données :**

1. Sélectionnez une source.
1. Sélectionnez un compte existant ou créez-en un.
1. Sélectionnez un type de données dans la liste des types disponibles à l’import à partir de la source.
1. Sélectionnez un jeu de données existant ou créez-en un.
1. Mappez les champs de la source au schéma.

   >[!NOTE]
   >
   >* Si vous mappez un type de schéma à un autre type identique, cette opération est effectuée automatiquement.
   >* Vous pouvez également importer le mappage à partir d’un autre flux du système.
   >* Vous pouvez mapper un champ Source à plusieurs champs de destination, mais le contraire est impossible.
   >* Vous pouvez créer des champs calculés ([fonctions de mappage de la préparation des données](https://experienceleague.adobe.com/docs/experience-platform/data-prep/functions.html?lang=fr){target="_blank"}).

   >[!CAUTION]
   >
   >* Vous pouvez modifier un flux de données, mais les données ne sont pas renvoyées lorsqu’un mappage est modifié.
   >* Si un champ obligatoire est NULL, le flux entier est rejeté.

   >[!NOTE]
   >
   >[Exigence d’intégrité des données de Marketo Measure Ultimate](/help/data-integrity-requirement.md){target="_blank"}

1. Définissez une cadence de chargement des données.
1. Vérifiez et validez.
1. Consultez la page « Statut du compte » dans les paramètres de l’interface utilisateur de mesure pour connaître le statut du flux de données.

**Surveillance :**

Page Sources > Flux de données pour vérifier le statut des flux de données

* Pour afficher les détails d’activité d’un jeu de données, cliquez simplement sur le jeu de données.
* Pour afficher les erreurs de flux de données, sélectionnez un flux de données, choisissez une exécution de flux de données, puis cliquez sur « Vue d’ensemble des diagnostics d’erreur ».

## Inspection des données {#data-inspection}

Option 1 : pour exécuter des requêtes directement à partir de l’interface utilisateur, accédez à l’onglet Requêtes sous Gestion des données.

![Option 1 : pour exécuter des requêtes directement à partir de l’interface utilisateur, accédez aux Requêtes](assets/marketo-guide-4.png)

Option 2 : [Télécharger et utiliser PSQL](https://experienceleague.adobe.com/docs/experience-platform/query/clients/psql.html?lang=fr){target="_blank"} (plus rapide et plus fiable).

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
>* Il est recommandé d’inclure un seul jeu de données par flux de données.
>* Les données d’une entité donnée (par exemple, un compte) provenant d’une source donnée ne peuvent entrer que dans un seul jeu de données. Chaque jeu de données ne peut être inclus que dans un seul flux de données. Les violations arrêtent le flux de données au moment de l’exécution.
>* Supprimez la destination entière dans AEP pour supprimer les données dans Measure. La désactivation arrête les nouvelles exportations de données et conserve les anciennes données.
>* La configuration de Measure sera pour la plupart identique, mais certaines parties, comme le mappage des étapes, auront un aspect différent.
>* Quelques heures sont nécessaires pour qu’un nouveau flux de données génère une exécution de flux, ces dernières se produisant à intervalles horaires réguliers.

Dans Measure, la devise par défaut doit être définie dans la section « Devise ».

* Si vous utilisez plusieurs devises, le schéma de taux de conversion de devise doit être renseigné dans AEP pour qu’il puisse être lu et utilisé pour les conversions.

**Mappage d’étape :**

Les étapes n’étant pas automatiquement importées à partir des données de l’utilisateur ou de l’utilisatrice, elles doivent être mappées manuellement.

* Les utilisateurs et utilisatrices peuvent mapper des étapes à partir de différentes sources.

![Les utilisateurs peuvent mapper des étapes provenant de différentes sources.](assets/marketo-guide-5.png)

Si les étapes ne sont pas mappées, le système ne fonctionnera pas, car les données ne pourront aller nulle part.

Si vous êtes client ou cliente Marketo Measure Ultimate et que vous avez défini votre objet de tableau de bord par défaut sur Contact, n’utilisez pas les deux champs ci-dessous, spécifiques au prospect ([en savoir plus ici](/help/data-integrity-requirement.md){target="_blank"}).

* b2b.personStatus
* b2b.isConverted

**Règles des personnes membres de la campagne**

Sélectionnez un jeu de données et définissez des règles pour chacun d’eux.

**Règles des événements d’expérience**

Choisissez un jeu de données et sélectionnez les types d’activités.

* Les activités personnalisées ne sont pas prises en charge.
* Si la clientèle a des activités qui ne correspondent pas aux options disponibles, nous vous suggérons de les classer comme « Moments intéressants » et d’utiliser des champs personnalisés pour les distinguer.

**Canaux hors ligne :**

* Nous n’élaborons pas de règles de mappage de canaux spécifiques aux jeux de données. Par conséquent, cela serait global.
* Nous devrons à terme faire correspondre le type de campagne CRM et le canal. Pour l’instant, nous pouvons toutefois mapper le nom du canal aux deux champs comme solution.
* **Règles de canal : les données renvoyées ne comportent pas de données de transition d’étapes.**

Les paramètres Touchpoint et Segment restent les mêmes.
