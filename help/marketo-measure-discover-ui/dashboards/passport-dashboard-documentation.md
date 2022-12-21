---
unique-page-id: 42762628
description: Documentation du tableau de bord des passeports - [!DNL Marketo Measure] - Documentation du produit
title: Documentation du tableau de bord des passeports
exl-id: 43cb01a8-d02e-4086-af57-d7ec9275f87a
source-git-commit: f13e55f009f33140ff36523212ed8b9ed5449a4d
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---

# Documentation du tableau de bord des passeports {#passport-dashboard-documentation}

Le tableau de bord des passeports permet aux marketeurs d’afficher les pistes/contacts et opportunités qui ont passé par chaque étape de pipeline pendant une période donnée.

Ce tableau de bord comporte deux mosaïques :

* Opportunités : Nombre d’enregistrements d’opportunité transmis à chaque étape au cours de la période donnée.
* Leads/Contacts : Nombre d’enregistrements de piste ou de contact transmis à chaque étape au cours de la période donnée.

>[!NOTE]
>
>Dans tous les tableaux de bord de Discover, un seul objet de personne, prospect ou contact, peut faire l’objet d’un rapport. Défini dans [!UICONTROL Paramètres] > [!UICONTROL Reporting] > [!UICONTROL Paramètres d’attribution] > [!UICONTROL Objet de tableau de bord par défaut].

Ce tableau de bord prend en charge les filtres suivants (tous les filtres s’appliquent aux deux mosaïques) :

* Date : sélectionnez la période.
* Canal : filtrer les enregistrements par canaux. Un enregistrement est associé à un canal si l’un de ses points de contact est associé au canal.
* Subchannel : filtrer les enregistrements par sous-canaux. Un enregistrement est associé à un sous-canal si l’un de ses points de contact est associé au sous-canal.
* Campagne : filtrer les enregistrements par campagnes. Un enregistrement est associé à une campagne si l’un de ses points de contact est associé à la campagne.
* Source de la campagne : filtrez les enregistrements par sources de campagne. Les sources d’exemple de campagne sont les mots-clés, BingAds, Facebook, LinkedIn, etc. Un enregistrement est associé à une source de campagne si l’un de ses points de contact est associé à la source de la campagne.
* Nom du compte CRM : filtrer les enregistrements par noms de compte CRM.
* Filtres de segments : filtrer les enregistrements par segments personnalisés. Un enregistrement est associé à un segment si l’un de ses points de contact est associé au segment.

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
