---
unique-page-id: 42762600
description: Documentation du tableau de bord des instantanés - [!DNL Marketo Measure] - Documentation du produit
title: Documentation du tableau de bord des instantanés
exl-id: 4dfc92d2-ccab-4726-a869-3ae32aa89a5f
feature: Reporting
source-git-commit: f8a37a996afefe78900e57e1eb166cdd50b5347f
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 2%

---

# Documentation du tableau de bord des instantanés {#snapshot-dashboard-documentation}

Le tableau de bord d’instantanés vous permet de visualiser l’état de votre CRM à tout moment, avec la distribution des enregistrements entre les phases de piste/contact et d’opportunité.

Ce tableau de bord comporte deux mosaïques :

* **Instantané de piste/contact :** Nombre d’enregistrements de piste ou de contact dans chaque étape à la date sélectionnée.

>[!NOTE]
>
>Dans tous les tableaux de bord de Discover, un seul objet de personne, prospect ou contact, peut faire l’objet d’un rapport. Défini dans [!UICONTROL Paramètres] > [!UICONTROL Reporting] > [!UICONTROL Paramètres d’attribution] > [!UICONTROL Objet de tableau de bord par défaut].

* **Instantané d’opportunité :** Le nombre d&#39;enregistrements d&#39;opportunité dans chaque étape à la date sélectionnée.

Ce tableau de bord prend en charge les filtres suivants (tous les filtres s’appliquent aux deux mosaïques) :

* Date d’instantané : sélectionnez la date d’instantané.
* Identifiant/nom du compte CRM : filtrez les enregistrements par identifiant ou nom de compte CRM.

>[!NOTE]
>
>Les suggestions n’affichent que les noms.

* Canal : filtrer les enregistrements par canaux. Un enregistrement est associé à un canal si l’un de ses points de contact est associé au canal.
* Sous-canal : filtrez les enregistrements par sous-canaux. Un enregistrement est associé à un sous-canal si l’un de ses points de contact est associé au sous-canal.
* Campagne : filtrez les enregistrements par campagnes. Un enregistrement est associé à une campagne si l’un de ses points de contact est associé à la campagne.
* Source de la campagne : filtrez les enregistrements par sources de la campagne. Exemples de sources de campagne : [!DNL Adwords], [!DNL BingAds], [!DNL Facebook], [!DNL LinkedIn], etc. Un enregistrement est associé à une source de campagne si l’un de ses points de contact est associé à la source de la campagne.
* Identifiant/nom du compte publicitaire : filtrez les enregistrements par identifiant ou nom de compte publicitaire. Un enregistrement est associé à un compte publicitaire si l’un de ses points de contact est associé à une campagne à partir des comptes publicitaires sélectionnés.

>[!NOTE]
>
>Les suggestions affichent uniquement les noms.

* Filtres de segments : filtrez les enregistrements par segments personnalisés. Un enregistrement est associé à un segment si l’un de ses points de contact est associé au segment.

La logique &quot;AND&quot; est utilisée sur tous les filtres.

>[!NOTE]
>
>Si un enregistrement change d’étape à la date sélectionnée, l’enregistrement est comptabilisé pour les scènes de et de , ainsi que pour toutes les étapes intermédiaires.

## Capture instantanée du lead/contact {#lead-contact-snapshot}

![](assets/one.png)

Les étapes comprennent les phases FT, LC et d’entonnoir sélectionnées dans les phases de piste/contact ouvertes ([!UICONTROL Paramètres] > [!UICONTROL CRM] > [!UICONTROL Mappage d’étape]).

Vous pouvez descendre dans chaque barre pour afficher les enregistrements de piste/contact pour chaque étape.

## Capture instantanée d’opportunités {#opportunity-snapshot}

![](assets/two.png)

Les étapes comprennent les phases FT, LC, d’entonnoir sélectionnées dans les phases de piste/contact ouvertes ([!UICONTROL Paramètres] > [!UICONTROL CRM] > [!UICONTROL Mappage d’étape]). Et les phases OC et d’entonnoir sélectionnées dans les phases d’ouverture des opportunités ([!UICONTROL Paramètres] > [!UICONTROL CRM] > [!UICONTROL Mappage d’étape]).

Vous pouvez descendre dans chaque barre pour afficher les enregistrements d’opportunité pour chaque étape.
