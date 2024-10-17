---
unique-page-id: 18874564
description: Définition des sessions web  [!DNL Marketo Measure]  -  [!DNL Marketo Measure]
title: Définition des sessions web  [!DNL Marketo Measure]
exl-id: ddf4f19d-2024-413a-b0ae-4efd468c24de
feature: Tracking
source-git-commit: 9a5e267b4b268d067fbbe89a00a4da96752a44db
workflow-type: tm+mt
source-wordcount: '811'
ht-degree: 65%

---

# Définition des sessions web [!DNL Marketo Measure] {#definition-of-marketo-measure-web-sessions}

Découvrez comment [!DNL Marketo Measure] définit les sessions web.

Une **session web** fait référence aux interactions d’une personne avec votre site Web pendant une certaine période. La session commence lorsqu’une personne arrive sur votre site Web.

Par exemple, Haley visite adobe.com/fr. Sa visite sur le site commence une session. Lorsque Haley quitte le site, en fermant l’onglet ou le navigateur Web ou en quittant le site, la session se termine.

Il n’est pas possible d’ouvrir plusieurs sessions en même temps. Si Haley ouvre [!DNL adobe.com] dans 10 onglets distincts, une seule session est créée en lien avec sa visite du site web.

## Comment [!DNL Marketo Measure] définit-il une nouvelle session ? {#how-does-marketo-measure-define-a-new-session}

Il existe plusieurs éléments qui déterminent le moment où une session se termine et le moment où une nouvelle session commence. Les deux principales façons dont les sessions [!DNL Marketo Measure] peuvent se terminer sont les suivantes :

* **Expiration basée sur le temps**
* **Expiration basée sur les canaux**

## Expiration basée sur le temps {#time-based-expiration}

### Comportement hérité {#legacy-behavior}

**Combien de temps dure une session ?**

Les sessions [!UICONTROL Marketo Measure] se termineront après 30 minutes d’inactivité sur le site web. Par exemple :

Lorsque Haley visite adobe.com/fr, une session commence. Elle explore le site pendant quelques minutes puis s’éloigne de son ordinateur, mais laisse le site ouvert. Après 30 minutes d’inactivité, la session se termine.

Actuellement, [!UICONTROL Marketo Measure] considère uniquement la navigation sur les pages et les envois de formulaire comme une activité. Le fait de faire défiler la page web ou de survoler un élément n’est pas considéré comme une activité. Ainsi, si Haley se rend sur adobe.com/fr pour lire un article de blog et qu’il lui faut une heure pour le lire, sa session web se terminera malgré tout après 30 minutes, même si elle fait défiler le contenu de la page.

### Nouveau comportement {#new-behavior}

Pour les nouveaux utilisateurs, il s’agit du comportement par défaut.

Les utilisateurs existants peuvent adopter le nouveau comportement en activant le bouton d’activation sous **Paramètres** > **Attribution tactile** > **Canal de session**. Une fois activé, ce paramètre ne peut pas être inversé.

Lorsqu’une nouvelle session est créée après 30 minutes d’inactivité, le canal de la session précédente est transféré si la nouvelle session commence dans les sept jours. Ce basculement s’applique uniquement aux visites directes (aucun référent ou référent interne). Si l’inactivité dépasse sept jours, le canal de la nouvelle session est Direct/Autre par défaut. Par exemple, si Haley visite landingpage.com depuis Google, est inactif pendant plus de 30 minutes et revient dans les sept jours, la nouvelle session conserve le canal Google. Cependant, si le même utilisateur consulte à nouveau la page via un autre canal, le canal non direct ne sera pas remplacé par le canal Google précédent.

Seul le canal sera rechargé, à l’exclusion des détails de campagne ou de référent. En effet, la classification des canaux est gérée par Marketo Measure, tandis que d’autres points de données sont collectés séparément.

**Connexion à Social**

Lorsqu’un visiteur utilise la connexion sociale via Google, Microsoft ou Apple, la session est fusionnée en une session continue. Par exemple, si un visiteur arrive sur une page à partir de LinkedIn, qu’il se connecte à un réseau social Google et qu’il atteint une page de remerciement, tous ces événements sont considérés comme une session unique. Si le basculement du canal de session n’est pas activé, la connexion sociale crée des sessions distinctes en raison du référent externe.

## Expiration basée sur les canaux {#channel-based-expiration}

[!DNL Marketo Measure] commence une nouvelle session chaque fois qu’un utilisateur ou une utilisatrice se rend sur votre site web à partir d’un autre canal marketing numérique ou d’un site web externe. Celle-ci vous permet de capturer les données suivantes :

* Site de référence
* Canaux sociaux ([!DNL Facebook], [!DNL LinkedIn], etc.)
* Canaux de référencement organique ou payants ([!DNL Google/Bing])

**Sites web de référence et canaux sociaux**

Chaque fois qu’un visiteur ou une visiteuse se rend sur votre site web à partir d’un site web de référence ou d’un canal social, une nouvelle session commence.

Imaginons que Haley soit sur LinkedIn, clique sur une publication [!DNL Marketo Measure], puis soit redirigée vers le site web d’Adobe. Ensuite, tout en faisant défiler [!DNL Facebook], Haley voit une autre publication [!DNL Marketo Measure]. Lorsqu’elle clique sur cette publication et qu’elle est redirigée vers le site d’Adobe, la première session web liée à [!DNL LinkedIn] se termine et une nouvelle session liée à [!DNL Facebook] commence.

**Canaux de référencement organique ou payants**

De nouvelles sessions démarrent chaque fois qu’un utilisateur ou une utilisatrice se rend sur votre site par le biais de canaux de référencement organique ou payants. Si Haley se rend sur le site web d’Adobe par le biais d’un référencement organique, puis visite immédiatement votre site web par le biais d’une publicité payante sur Google, deux sessions distinctes sont créées.

**Trafic direct web**

Si une personne se rend sur votre site Web en saisissant l’URL de celui-ci dans la barre d’adresse, une nouvelle session n’est pas toujours entamée pour autant.

Si la première session web de Haley débute à la suite d’une visite d’un site de référence, d’un canal de réseau social ou d’un canal de référencement organique/payant, puis qu’elle se rend sur le site par le biais d’un lien direct web, une nouvelle session n’est pas entamée pour autant.

_Cependant_, si la première session web de Haley provient d’un lien direct web, puis qu’elle visite le site web via _un site externe/de référence_, la première session se termine et une nouvelle session est ouverte en rapport avec le site externe/de référence.

## Sessions Google Analytics {#google-analytics-sessions}

Il existe des similitudes avec la manière dont [!DNL Marketo Measure] et Google Analytics définissent les sessions. Pour plus d’informations sur la façon dont Google Analytics définit les sessions, consultez la page : [https://support.google.com/analytics/answer/2731565?hl=fr](https://support.google.com/analytics/answer/2731565?hl=fr){target="_blank"}
