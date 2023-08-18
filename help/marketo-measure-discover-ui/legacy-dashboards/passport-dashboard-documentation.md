---
unique-page-id: 42762628
description: Documentation du tableau de bord des passeports - [!DNL Marketo Measure] - Documentation du produit
title: Documentation du tableau de bord des passeports
exl-id: 43cb01a8-d02e-4086-af57-d7ec9275f87a
feature: Reporting
source-git-commit: f8a37a996afefe78900e57e1eb166cdd50b5347f
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 2%

---

# Documentation du tableau de bord des passeports {#passport-dashboard-documentation}

Le tableau de bord des passeports permet aux marketeurs d’afficher les pistes/contacts et opportunités qui ont passé par chaque étape de pipeline au cours d’une période donnée.

Ce tableau de bord comporte deux mosaïques :

* Opportunités : nombre d’enregistrements d’opportunité transmis au cours de chaque étape au cours de la période donnée.
* Pistes/Contacts : nombre d’enregistrements de piste ou de contact transmis à chaque étape au cours d’une période donnée.

>[!NOTE]
>
>Dans tous les tableaux de bord de Discover, un seul objet de personne, prospect ou contact, peut faire l’objet d’un rapport. Défini dans [!UICONTROL Paramètres] > [!UICONTROL Reporting] > [!UICONTROL Paramètres d’attribution] > [!UICONTROL Objet de tableau de bord par défaut].

Ce tableau de bord prend en charge les filtres suivants (tous les filtres s’appliquent aux deux mosaïques) :

* Date : sélectionnez la période.
* Canal : filtrer les enregistrements par canaux. Un enregistrement est associé à un canal si l’un de ses points de contact est associé au canal.
* Sous-canal : filtrez les enregistrements par sous-canaux. Un enregistrement est associé à un sous-canal si l’un de ses points de contact est associé au sous-canal.
* Campagne : filtrez les enregistrements par campagnes. Un enregistrement est associé à une campagne si l’un de ses points de contact est associé à la campagne.
* Source de la campagne : filtrez les enregistrements par sources de la campagne. Les sources d’exemple de campagne sont les mots-clés, BingAds, Facebook, LinkedIn, etc. Un enregistrement est associé à une source de campagne si l’un de ses points de contact est associé à la source de la campagne.
* Nom du compte CRM : filtrez les enregistrements par nom de compte CRM.
* Filtres de segments : filtrez les enregistrements par segments personnalisés. Un enregistrement est associé à un segment si l’un de ses points de contact est associé au segment.

La logique &quot;AND&quot; est utilisée sur tous les filtres.

>[!NOTE]
>
>Si un enregistrement change d’étape à la date sélectionnée, l’enregistrement est comptabilisé pour les scènes de et de , ainsi que pour toutes les étapes intermédiaires.

## Opportunités {#opportunities}

![](assets/one-1.png)

Les étapes incluent OC, les étapes d’entonnoir sélectionnées dans les étapes d’ouverture d’opportunité ([!UICONTROL Paramètres] > [!UICONTROL CRM] > [!UICONTROL Mappage d’étape]), et les phases d’opportunité gagnantes ([!UICONTROL Paramètres] > [!UICONTROL CRM] > [!UICONTROL Mappage d’étape]).

>[!NOTE]
>
>Pour les scènes Gagnantes, les décomptes d’enregistrements ne sont disponibles que pour les enregistrements transférés dans l’étape au cours de la période sélectionnée.

Vous pouvez descendre dans chaque barre pour afficher les enregistrements d’opportunité pour chaque étape.

## Leads/contacts {#leads-contacts}

![](assets/two-1.png)

Les étapes comprennent les phases FT, LC, d’entonnoir sélectionnées dans les étapes Ouvrir le prospect/Contact sur les paramètres - CRM - Mappage dans l’environnement intermédiaire et les étapes de piste/contact converties sur les paramètres - CRM - Mappage dans l’environnement intermédiaire.

>[!NOTE]
>
>Pour les scènes converties, les décomptes d’enregistrements ne sont disponibles que pour les enregistrements transférés dans l’étape au cours de la période sélectionnée.

Vous pouvez descendre dans chaque barre pour afficher les enregistrements de piste/contact pour chaque étape.
