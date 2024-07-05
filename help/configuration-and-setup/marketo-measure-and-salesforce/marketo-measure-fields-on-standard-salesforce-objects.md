---
unique-page-id: 18874574
description: « Champs [!DNL Marketo Measure] sur les objets  [!DNL Salesforce]  standard -  [!DNL Marketo Measure] »
title: « Champs [!DNL Marketo Measure] sur les objets  [!DNL Salesforce]  standard »
exl-id: c9d5254f-06bd-4813-bb29-1a4955b37041
feature: Salesforce
source-git-commit: 05ba9e487d492ba4352a7f0577c7221f6ec9567e
workflow-type: ht
source-wordcount: '670'
ht-degree: 100%

---

# « Champs [!DNL Marketo Measure] sur les objets [!DNL Salesforce] standard » {#marketo-measure-fields-on-standard-salesforce-objects}

>[!NOTE]
>
>Des instructions spécifiant « [!DNL Marketo Measure] » peuvent s’afficher dans la documentation tandis que votre CRM peut mentionner « Bizible ». Nous nous efforçons de mettre cela à jour. Notre nouvelle identité de marque (rebranding) sera bientôt répercutée dans votre CRM.

Découvrez les différents champs [!DNL Marketo Measure] ajoutés aux objets standards [!DNL Salesforce].

## Compte {#account}

Score d’engagement prédictif : ce champ est utilisé avec notre fonction ABM pour fournir un score lié à l’engagement du compte et prend en compte de nombreux facteurs tels que la date des consultations de pages, le nombre de contacts associés au compte, le fait qu’une opportunité est fermée, etc.

## Campagne {#campaign}

Seuls 4 champs sont ajoutés, 1 bouton et 1 règle de validation.

UniqueID : ce champ est utilisé en interne pour nous permettre d’effectuer un suivi des différentes campagnes synchronisées avec [!DNL Marketo Measure].

Activer Buyer Touchpoints : ce champ sert à synchroniser les campagnes pour l’inclusion de l’attribution hors ligne et des données historiques.

Date de début du point de contact : ce champ permet de définir la date de début d’application de points de contact aux campagnes historiques.

Date de fin du point de contact : ce champ permet de définir la date de fin d’application de points de contact aux campagnes historiques. Un exemple courant serait l’inclusion de campagnes numériques antérieures à [!DNL Marketo Measure] et la définition de la date de fin sur le jour où le script a été appliqué.

Mise à jour en bloc de la date du point de contact (bouton) : ce bouton permet de gérer la date du point de contact des personnes membres de la campagne lors de la synchronisation de la campagne, car par défaut, nous ferons référence soit à la date d’abonnement à la campagne, soit à la date de la première réponse. Dans le cas où ces champs de date ne seraient pas une représentation exacte de la date réelle du point de contact, nous utiliserions ce bouton pour définir la date du point de contact.

Mise à jour de l’attribution [!DNL Marketo Measure] (règle de validation) : cette règle est obsolète depuis la version 6.0 du package.

## Personne membre de la campagne {#campaign-member}

5 champs et 1 déclencheur Apex ont été ajoutés au package.

Statut du point de contact (Prospect) : il s’agit d’un champ de diagnostic lié à une fonctionnalité qui n’est pas activée initialement. Nous l’utilisons pour savoir si un point de contact a été créé par rapport à l’enregistrement de prospect correspondant ou, si ce n’est pas le cas, pour en connaître la raison.

Statut du point de contact (Contact) : il s’agit d’un champ de diagnostic lié à une fonctionnalité qui n’est pas activée initialement. Nous l’utilisons pour savoir si un point de contact a été créé par rapport à l’enregistrement de contact correspondant ou, si ce n’est pas le cas, pour en connaître la raison.

Statut du point de contact (Opportunité) : il s’agit d’un champ de diagnostic lié à une fonctionnalité qui n’est pas activée initialement. Nous l’utilisons pour savoir si un point de contact a été créé par rapport à l’enregistrement d’opportunité correspondant ou, si ce n’est pas le cas, pour en connaître la raison.

Date de statut du point de contact : il s’agit de la date à laquelle les champs de diagnostic ont été renseignés.

Date du Buyer Touchpoint : lié au bouton [!UICONTROL Mise à jour en bloc de la date du point de contact] de l’objet Campagne. Lorsqu’il est utilisé, nous appliquons la date du point de contact définie à la personne membre de la campagne.

OnCampaignMemberDelete : [!DNL Salesforce] n’apparaît pas initialement lorsque des personnes membres de la campagne sont supprimées, ce qui peut entraîner des problèmes de précision dans les rapports d’attribution. Lorsqu’une personne membre de la campagne est supprimée, cette action est déclenchée pour demander à [!DNL Marketo Measure] de supprimer les points de contact liés à cette personne membre de la campagne qui n’existe plus.

## Lead {#lead}

Le champ Compte Bizible est utilisé pour le mappage d’un lead à un compte dans le cadre de notre fonctionnalité ABM. Nous renseignons ce champ pour créer la relation de consultation entre les deux objets.

## Compte {#account-1}

Cette information est utilisée pour le mappage d’un prospect à un compte dans le cadre de notre fonctionnalité ABM. Nous renseignons ce champ pour créer la relation de consultation entre les deux objets.

## Opportunité {#opportunity}

Montant de l’opportunité [!DNL Marketo Measure] : ce champ est utilisé lorsqu’un champ de montant personnalisé est utilisé dans l’opportunité. Nous mappons la valeur de ce champ personnalisé au montant de l’opportunité [!DNL Marketo Measure] à l’aide d’un workflow, puis nous lisons ce champ pour nos champs d’attribution de revenus sur l’objet Buyer Attribution Touchpoint.

## Activité {#activity}

BizibleID : cette information nous permet de relier un point de contact à des activités pour notre attribution d’activités et l’intégration de mesures de suivi des appels.

Date du Buyer Touchpoint : il s’agit d’un champ qui peut être rempli via un workflow, à utiliser comme date pour l’attribution des activités. Il sera rempli pour notre intégration de calltrackingmetrics afin de savoir à quel moment a eu lieu l’interaction.
