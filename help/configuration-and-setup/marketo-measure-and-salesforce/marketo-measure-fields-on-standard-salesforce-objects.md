---
unique-page-id: 18874574
description: "[!DNL Marketo Measure] Champs dans Standard [!DNL Salesforce] Objets - [!DNL Marketo Measure] - Documentation du produit"
title: "[!DNL Marketo Measure] Champs dans Standard [!DNL Salesforce] Objets"
exl-id: c9d5254f-06bd-4813-bb29-1a4955b37041
source-git-commit: b910e5aedb9e178058f7af9a6907a1039458ce7a
workflow-type: tm+mt
source-wordcount: '1285'
ht-degree: 0%

---

# [!DNL Marketo Measure] Champs dans Standard [!DNL Salesforce] Objets {#marketo-measure-fields-on-standard-salesforce-objects}

>[!NOTE]
>
>Vous pouvez voir des instructions spécifiant &quot;[!DNL Marketo Measure]&quot; dans notre documentation, mais consultez toujours &quot;Bizible&quot; dans votre CRM. Nous nous efforçons de mettre à jour cette version et la nouvelle image sera bientôt répercutée dans votre CRM.

En savoir plus sur les différentes [!DNL Marketo Measure] champs ajoutés à [!DNL Salesforce] objets standard.

## Compte {#account}

Score d’engagement prédictif : Ce champ est utilisé avec notre fonction ABM pour fournir un score en fonction de l’engagement du compte et prend en compte de nombreux facteurs tels que la récence des pages vues, le nombre de contacts associés au compte, l’existence d’une option fermée, etc.

## Dossier {#case}

Nous ajoutons des champs à l’objet Cas associé aux jalons Première touche et Création de piste. Il s’agit pour les clients qui utilisent l’objet Cas au lieu de l’prospect ou du contact et qui ont également pour but d’afficher les données d’une autre manière lorsqu’un client ne souhaite pas que nous créions d’enregistrements de point de contact.

Source du point de contact (FT) : Il s’agit de la source de l’interaction Première touche.

Source du point de contact (LC) : Il s’agit de la source de l’interaction tactile de création de piste.

Canal marketing (FT) : Il s’agit du canal marketing de l’interaction Première touche.

Canal marketing (LC) : Il s’agit du canal marketing de l’interaction tactile de création de piste.

Nom de la campagne publicitaire (FT) : Il s’agit de la campagne UTM, de la campagne publicitaire des réseaux publicitaires, ou [!DNL Salesforce] Campagne de l’interaction Première touche.

Nom de la campagne publicitaire (LC) : Il s’agit de la campagne UTM, de la campagne publicitaire des réseaux publicitaires, ou [!DNL Salesforce] Campagne du [!UICONTROL création de piste] interaction tactile.

Landing Page (FT) : Il s’agit de la page d’entrée de l’interaction Première touche.

Landing Page (LC) : Il s’agit de la page d’entrée de la variable [!UICONTROL création de piste] interaction tactile.

Date du point de contact (FT) : Il s’agit de la date de l’interaction Première touche.

Date du point de contact (LC) : Il s’agit de la date de l’interaction tactile de création de piste.

## Campagne {#campaign}

Seuls 4 champs ont été ajoutés, 1 bouton et 1 règle de validation.

UniqueID : Ce champ est utilisé en interne pour effectuer le suivi des différentes campagnes synchronisées avec [!DNL Marketo Measure].

Activer les points de contact d’achat : Ce champ est destiné à la synchronisation réelle des campagnes pour l’inclusion de l’attribution hors ligne et les données historiques.

Date de début du point de contact : Ce champ permet de définir la date de début de l’application des points de contact aux campagnes historiques.

Date de fin du point de contact : Ce champ permet de définir une date de fin pour l’application des points de contact aux campagnes historiques. Un exemple courant est l’inclusion de campagnes numériques avant[!DNL Marketo Measure] puis définir la date de fin comme jour d’application du script.

Date de point de contact de mise à jour en bloc (bouton) : Ce bouton permet de gérer la date du point de contact des membres de la campagne lors de la synchronisation de celle-ci, car nous allons référencer soit la date d’adhésion à la campagne, soit la date de la première réponse prête à l’emploi. Si ces champs de date ne représentent pas de manière exacte la date réelle du point de contact, nous utiliserons ce bouton pour définir la date du point de contact.

Mettre à jour [!DNL Marketo Measure] Attribution (règle de validation) : Cette règle est obsolète après la version 6.0 du package.

## Membre de la campagne {#campaign-member}

Il y a 5 champs et 1 déclencheur d’application ajouté avec le package.

État du point de contact (piste) : Il s’agit d’un champ de diagnostic associé à une fonctionnalité qui n’est pas activée en standard. Nous l’utilisons pour comprendre si un point de contact a été créé par rapport à l’enregistrement de piste associé ou, dans le cas contraire, pourquoi.

État du point de contact (Contact) : Il s’agit d’un champ de diagnostic associé à une fonctionnalité qui n’est pas activée en standard. Nous l’utilisons pour comprendre si un point de contact a été créé par rapport à l’enregistrement Contact associé ou, dans le cas contraire, pourquoi.

État du point de contact (opportunité) : Il s’agit d’un champ de diagnostic associé à une fonctionnalité qui n’est pas activée en standard. Nous l’utilisons pour comprendre si un point de contact a été créé par rapport à l’enregistrement d’opportunité associé ou, dans le cas contraire, pourquoi.

Date d’état du point de contact : Il s’agit de la date à laquelle les champs de diagnostic ont été renseignés.

Date de point de contact de l’acheteur : Il est lié au [!UICONTROL Date de point de contact de mise à jour en bloc] à partir de l’objet Campaign. Lorsqu&#39;elle est utilisée, nous appliquons la date de point de contact définie au membre de campagne.

OnCampaignMemberDelete : Prêt à l’emploi, [!DNL Salesforce] ne s’affiche pas lorsque des membres de campagne sont supprimés, ce qui peut entraîner des problèmes avec des rapports d’attribution précis. Lorsqu&#39;un membre de Campaign est supprimé, il est déclenché pour informer : [!DNL Marketo Measure] pour supprimer les points de contact liés à ce membre de campagne inexistant.

## Contact {#contact}

Nous ajoutons des champs à l’objet Contact liés aux jalons Première touche et Création de piste. Cela est destiné aux clients qui préfèrent que l’attribution soit rapportée directement aux champs plutôt que de créer des enregistrements de point de contact. La plupart de nos clients utilisent l’itinéraire des enregistrements Touchpoint, mais également ces champs dans leur plateforme d’automatisation.

Source du point de contact (FT) : Il s’agit de la source de l’interaction Première touche.

Source du point de contact (LC) : Il s’agit de la source de l’interaction tactile de création de piste.

Canal marketing (FT) : Il s’agit du canal marketing de l’interaction Première touche.

Canal marketing (LC) : Il s’agit du canal marketing de l’interaction tactile de création de piste.

Nom de la campagne publicitaire (FT) : Il s’agit de la campagne UTM, de la campagne publicitaire des réseaux publicitaires, ou [!DNL Salesforce] Campagne de l’interaction Première touche.

Nom de la campagne publicitaire (LC) : Il s’agit de la campagne UTM, de la campagne publicitaire des réseaux publicitaires, ou [!DNL Salesforce] Campagne du [!UICONTROL création de piste] interaction tactile.

Landing Page (FT) : Il s’agit de la page d’entrée de l’interaction Première touche.

Landing Page (LC) : Il s’agit de la page d’entrée de la variable [!UICONTROL création de piste] interaction tactile.

Date du point de contact (FT) : Il s’agit de la date de l’interaction Première touche.

Date du point de contact (LC) : Il s’agit de la date de l’interaction tactile de création de piste.

BizibleID : Il est utilisé par rapport à l’intégration des mesures d’attribution et de suivi des activités pour l’association Contact au point de contact.

## Lead {#lead}

Nous ajoutons des champs à l’objet Lead liés aux jalons Première touche et Création de piste. Cela est destiné aux clients qui préfèrent que l’attribution soit rapportée directement aux champs plutôt que de créer des enregistrements de point de contact. La plupart de nos clients utilisent l’itinéraire des enregistrements Touchpoint, mais également ces champs dans leur plateforme d’automatisation.

Source du point de contact (FT) : Il s’agit de la source de l’interaction Première touche.

Source du point de contact (LC) : Il s’agit de la source de l’interaction tactile de création de piste.

Canal marketing (FT) : Il s’agit du canal marketing de l’interaction Première touche.

Canal marketing (LC) : Il s’agit du canal marketing de l’interaction tactile de création de piste.

Nom de la campagne publicitaire (FT) : Il s’agit de la campagne UTM, de la campagne publicitaire des réseaux publicitaires, ou [!DNL Salesforce] Campagne de l’interaction Première touche.

Nom de la campagne publicitaire (LC) : Il s’agit de la campagne UTM, de la campagne publicitaire des réseaux publicitaires, ou [!DNL Salesforce] Campagne de l’interaction tactile de création de piste.

Landing Page (FT) : Il s’agit de la page d’entrée de l’interaction Première touche.

Landing Page (LC) : Il s’agit de la page d’entrée de l’interaction tactile de création de piste.

Date du point de contact (FT) : Il s’agit de la date de l’interaction Première touche.

Date du point de contact (LC) : Il s’agit de la date de l’interaction tactile de création de piste.

BizibleID : Il est utilisé par rapport à l’intégration des mesures d’attribution et de suivi des activités pour l’association de piste au point de contact.

## Compte {#account-1}

Il est utilisé pour notre mappage de piste au compte pour notre fonctionnalité ABM. Nous renseignons ce champ pour créer la relation de recherche entre les deux objets.

## Opportunité {#opportunity}

[!DNL Marketo Measure] Montant de l&#39;opportunité : Ce champ est utilisé dans le scénario où un champ de montant personnalisé est utilisé sur l’opportunité. Nous associons cette valeur de champ personnalisée à [!DNL Marketo Measure] Montant de l’opportunité à l’aide d’un workflow, puis lisez ce champ pour nos champs d’attribution Recettes sur l’objet Point de contact d’attribution de l’achat.

## Activité {#activity}

BizibleID : Cela nous permet d’établir un lien entre un point de contact et les activités pour l’intégration des mesures d’attribution des activités et de suivi des appels.

Date de point de contact de l’acheteur : Il s’agit d’un champ qui peut être renseigné via un workflow à utiliser comme date d’attribution des activités. Il sera renseigné pour l’intégration de nos mesures de suivi des appels afin de savoir quand l’interaction s’est produite.
