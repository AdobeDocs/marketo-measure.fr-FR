---
unique-page-id: 18874564
description: Définition de [!DNL Marketo Measure] Sessions web - [!DNL Marketo Measure] - Documentation du produit
title: Définition de [!DNL Marketo Measure] Sessions web
exl-id: ddf4f19d-2024-413a-b0ae-4efd468c24de
source-git-commit: ae5b77744d523606ce6cfcf48d7e8d5049d5ccb7
workflow-type: tm+mt
source-wordcount: '579'
ht-degree: 0%

---

# Définition de [!DNL Marketo Measure] Sessions web {#definition-of-marketo-measure-web-sessions}

Découvrez comment [!DNL Marketo Measure] définit les sessions web.

A **session web** fait référence aux interactions d’une personne avec votre site web pendant une certaine période. La session commence lorsqu’un utilisateur arrive sur votre site web.

Par exemple, Haley visite adobe.com. Sa visite sur le site commence une session. Lorsque Haley quitte le site, en fermant l’onglet ou le navigateur Web ou en quittant le site, la session se termine.

Un utilisateur ne peut pas ouvrir plusieurs sessions en même temps. Si Halte s’ouvre [!DNL adobe.com] dans 10 onglets distincts, une seule session a été créée en relation avec sa visite du site web.

## Comment [!DNL Marketo Measure] définir une nouvelle session ? {#how-does-marketo-measure-define-a-new-session}

Il existe plusieurs éléments qui déterminent le moment où une session se termine et le moment où une nouvelle session commence. Les deux principaux moyens [!DNL Marketo Measure] Les sessions peuvent se terminer comme suit :

* **Expiration basée sur le temps**
* **Expiration basée sur les canaux**

## Expiration basée sur le temps {#time-based-expiration}

**Combien de temps dure une session ?**

[!DNL Marketo Measure] les sessions se terminent après 30 minutes d’inactivité sur le site web. Par exemple :

Lorsque Haley visite adobe.com, une session commence. Elle explore le site pendant quelques minutes puis s&#39;éloigne de son ordinateur, mais laisse le site ouvert. Après 30 minutes d’inactivité, la session se termine.

Actuellement, [!DNL Marketo Measure] ne considère que la navigation dans les pages et les envois de formulaire comme une activité. Le fait de faire défiler la page web ou de survoler un élément de la page n’est pas considéré comme une activité. Ainsi, si Haley se rend sur adobe.com pour lire un billet de blog, et qu&#39;il lui faut une heure pour le lire, sa session web se termine toujours après 30 minutes, même si elle fait défiler le contenu de la page.

## Expiration basée sur les canaux {#channel-based-expiration}

[!DNL Marketo Measure] commence une nouvelle session chaque fois qu’un utilisateur se rend sur votre site web à partir d’un autre canal de marketing numérique ou d’un site web externe. Celle-ci vous permet de capturer les données suivantes :

* Un site de référence
* Canaux sociaux ([!DNL Facebook], [!DNL LinkedIn], etc.)
* Canaux de recherche payants ou organiques ([!DNL Google/Bing])

**Sites web de référence et canaux sociaux**

Chaque fois qu’un visiteur se rend sur votre site web à partir d’un site web de référence ou d’un canal social, une nouvelle session commence.

Dites que Haley est sur LinkedIn, cliquez sur un [!DNL Marketo Measure] et est redirigé vers le site web d’Adobe. Ensuite, lorsque vous faites défiler [!DNL Facebook], Haley en voit une autre [!DNL Marketo Measure] post. Lorsqu’elle clique sur cette publication et qu’elle est redirigée vers le site de l’Adobe, la première session Web liée à [!DNL LinkedIn] à la fin et une nouvelle session liée à [!DNL Facebook] commence.

**Canaux de recherche payants ou organiques**

De nouvelles sessions démarrent chaque fois qu’un utilisateur se rend sur votre site par le biais de canaux de recherche payante ou organique. Si Haley se rend sur le site web de l’Adobe par le biais de la recherche organique, puis visite immédiatement votre site web par le biais d’une publicité payante sur Google, deux sessions distinctes sont créées.

**Trafic direct Web**

Si un visiteur se rend sur votre site Web en saisissant l’URL de celui-ci dans la barre d’adresse, une nouvelle session ne commence pas toujours.

Si la première session web de Haley débute à la suite d’une visite d’un site de référence, d’un canal de réseau social ou d’un canal de recherche payante/organique, puis qu’elle se rend sur le site par le biais d’un lien Web direct, cela n’entraîne pas le début d’une nouvelle session.

_Cependant_, si la première session web de Haley provient de Web Direct, puis qu’elle visite le site web via _un site externe/de référence_, la première session se termine et une nouvelle session est ouverte en rapport avec le site externe/de référence.

## Sessions Google Analytics {#google-analytics-sessions}

Il existe des similitudes avec la manière dont [!DNL Marketo Measure] et les Google Analytics définissent les sessions. Pour plus d’informations sur la façon dont les Google Analytics définissent les sessions, consultez la page : [https://support.google.com/analytics/answer/2731565?hl=en](http://support.google.com/analytics/answer/2731565?hl=en){target="_blank"}
