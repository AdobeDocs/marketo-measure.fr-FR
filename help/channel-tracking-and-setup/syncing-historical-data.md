---
description: Conseils sur la synchronisation des données historiques pour les utilisateurs de Marketo Measure
title: Synchronisation des données historiques
exl-id: 5a3c1a71-463a-4d75-98b9-fc225839512a
feature: Channels
source-git-commit: fcd8e276c85669ddf12bd7404fb12d3e99b2642a
workflow-type: tm+mt
source-wordcount: '1540'
ht-degree: 3%

---

# Synchronisation des données historiques {#syncing-historical-data}

[!DNL Marketo Measure] est une solution qui fournit les données les plus granulaires et exploitables. Nous comprenons toutefois que vous pouvez avoir des données existantes pour lesquelles vous souhaitez que l’attribution soit activée. Il est possible de générer des points de contact pour les données historiques, mais il est important de prendre en compte certains facteurs avant d’aller de l’avant avec ce processus.

>[!NOTE]
>
>Cet article traite d’un processus obsolète. Nous encourageons les utilisateurs et les utilisatrices à utiliser le [nouveau processus in-app amélioré](/help/channel-tracking-and-setup/custom-campaign-sync.md){target="_blank"}.

## Facteurs à prendre en compte {#factors-to-consider}

**Les données sont-elles déjà organisées en campagnes ?**

a. Les données doivent être organisées en campagnes à synchroniser avec [!DNL Marketo Measure] pour que les points de contact soient générés. Si elle n’est pas actuellement organisée en campagnes, vous voudrez évaluer si le temps et les ressources nécessaires pour segmenter les données dans les campagnes appropriées sont suffisants.

b. La date à laquelle le membre a été ajouté à la campagne ou marqué comme ayant répondu sera utilisée pour la date du point de contact. Cette information doit donc également être exacte. [!DNL Marketo Measure] offre des solutions de contournement dans SFDC et MSD pour mettre à jour les dates, mais cela peut prendre du temps en fonction du volume.

**Disposez-vous d’une quantité de données assez égale organisée en campagnes pour tous les canaux (référencement payant, événements, organique, etc.) ?**

Il est important d’avoir une image équilibrée de l’attribution afin d’avoir des rapports exacts et « équitables ». Par exemple, si vous disposez uniquement de données pour des efforts hors ligne historiques de canal tels que les Événements, les données seront intrinsèquement biaisées sans données en ligne historiques pour les compléter.

**À quel niveau de granularité vous attendez-vous ?**

Vous ne connaîtrez essentiellement que le nom du canal, du sous-canal et de la campagne.

**Quels sont vos objectifs en matière de reporting à l’avenir ?**

Ces données vont être limitées, il est donc important de réfléchir à la façon dont vous prévoyez les utiliser. Il n’est peut-être pas très logique de comparer des données historiques à des données futures.

**Jusqu&#39;où voulez-vous remonter ?**

[!DNL Marketo Measure] recommande vivement de ne pas dépasser l&#39;année précédente.

C’est un sujet dont nous vous encourageons vivement à discuter d’abord avec votre contact [!DNL Marketo Measure]. Si vous avez pris en compte ce qui précède et souhaitez continuer, des instructions générales (séparées pour [!DNL Salesforce] et [!DNL Microsoft Dynamics]) sont ci-dessous.

## Synchronisation des campagnes historiques dans [!DNL Salesforce] {#syncing-historic-campaigns-in-salesforce}

**En ligne:**

Pour synchroniser les données en ligne historiques, les données doivent être organisées en campagnes Salesforce que vous synchroniserez ensuite avec [!DNL Marketo Measure] à l’aide des règles de synchronisation des campagnes [!DNL Salesforce] dans l’application [!DNL Marketo Measure]. Il est important de s’assurer que les points de contact ne sont générés à partir d’aucune de ces campagnes après la date de mise en ligne de votre JavaScript. La raison en est d’éviter les points de contact en double. Une fois le JavaScript en ligne, les efforts en ligne font l’objet d’un suivi automatique. Nous ne voulons donc pas les suivre également via une campagne SFDC. Pour éviter ce problème, veillez à ajouter une notion du temps à la règle. Peut-être qu’un élément tel que « La date de création du membre de la campagne est inférieure à la date de mise en production de [JavaScript »].

![Pour synchroniser les données en ligne historiques, les données doivent être organisées dans Salesforce](assets/dynamics-lists-1.png)

Le composant de mappage des canaux pour les données en ligne historiques peut être un peu difficile. Nous voulons qu’il corresponde le plus possible à vos règles de canaux en ligne actuelles (de la feuille de règles en ligne) pour des rapports épurés. Vous trouverez ci-dessous un exemple de mappage de canal idéal.

>[!NOTE]
>
>Ce mappage de canal est effectué dans la section [!UICONTROL Canaux hors ligne] de l’application [!DNL Marketo Measure], car nous utilisons des campagnes SFDC.

| Type de campagne Salesforce | Canal | Sous-canal |
|---|---|---|
| Recherche payante - AdWords | Recherche payante | AdWords |
| Référencement Payant - Bing | Recherche payante | Bing |
| Référencement Payant - Yahoo | Recherche payante | Yahoo |

Les données en ligne ajoutées de cette manière seront intrinsèquement moins granulaires que les données en ligne [!DNL Marketo Measure] les pistes via JavaScript. Par exemple, les champs tels que l’URL du formulaire, la page de destination, la page du référent, etc. ne seront pas renseignés. Par conséquent, il est recommandé de répartir les campagnes dans chaque source si possible. Comme illustré dans l’exemple ci-dessus, vous devez disposer de plusieurs types de campagne pour chaque source afin d’obtenir une granularité dans les rapports.

Il n’est peut-être pas possible ou raisonnable de disposer du nombre de types de campagne SFDC pour prendre en charge le mappage de canal granulaire. Vous pouvez donc avoir recours au mappage au niveau du canal et ignorer les sous-canaux. Si le niveau du canal n’est pas connu non plus, vous pouvez configurer un canal proxy tel que « Historic Digital » afin de savoir au moins qu’il s’agit d’une touche en ligne.

Si vous devez modifier en masse la date de point de contact qui sera transmise pour ces efforts en ligne historiques, utilisez le bouton [!DNL Marketo Measure] personnalisé « [!UICONTROL Date de point de contact de mise à jour en bloc] » (disponible sous la forme d’un champ personnalisé dans l’objet Campaign de SFDC). Si la durée de la campagne est courte, il peut être utile de modifier en masse la date du point de contact un jour par jour, tandis qu’il peut être judicieux de procéder à une mise à jour en masse une fois par semaine si la campagne dure plus longtemps. Si vous utilisez la fonctionnalité de mise à jour en bloc de la date de point de contact , veillez à mettre à jour la règle de synchronisation de la campagne pour utiliser la date Buyer Touchpoint dans le champ de date. Notez que vous devrez peut-être faire preuve de créativité avec vos règles de synchronisation de campagne si cela s’applique uniquement à une ou deux campagnes et pas à toutes.

**Hors ligne:**

Les données historiques des efforts de marketing hors ligne (celles qui ne peuvent pas être suivies via JavaScript) devront également être organisées en campagnes SFDC. Les campagnes SFDC permettent de suivre [!DNL Marketo Measure] efforts hors ligne, que l’activité soit « historique » ou « implémentation actuelle/post-[!DNL Marketo Measure] ». Vous devez donc suivre le même mappage de canal que celui décidé dans la formation originale Configuration de canal hors ligne .

Si nécessaire, utilisez le bouton « Mettre à jour la date de point de contact en bloc » pour modifier en masse la date de point de contact pour les membres de la campagne. Par exemple, si vous créez des campagnes SFDC après que l’événement s’est produit, vous souhaiterez effectuer des modifications en masse pour la date correcte. Si vous utilisez la fonctionnalité de mise à jour en bloc de la date de point de contact , veillez à mettre à jour la règle de synchronisation de la campagne pour utiliser la date Buyer Touchpoint dans le champ de date. Notez que vous devrez peut-être faire preuve de créativité avec vos règles de synchronisation de campagne si cela s’applique uniquement à une ou deux campagnes et pas à toutes.

## Synchronisation des campagnes historiques dans [!DNL Dynamics] {#syncing-historic-campaigns-in-dynamics}

[!DNL Marketo Measure] peut générer rétroactivement des points de contact pour les interactions qui se sont produites dans le passé, à condition qu’ils soient organisés en campagnes dans [!DNL Dynamics].

Cela implique généralement de travailler dans le CRM pour tenir compte des dates historiques. La gestion sera également différente pour les efforts en ligne (suivis par JS) et les efforts hors ligne (qui ne peuvent pas être suivis par JS).

Suivez les instructions ci-dessous pour organiser les données historiques dans [!DNL Dynamics] dans un format synchronisable avec [!DNL Marketo Measure].

**En ligne:**

Les données numériques historiques doivent être organisées en campagnes [!DNL Dynamics] pour être renvoyées. Idéalement, cette structure est déjà en place.

Si les données sont hébergées ailleurs (par exemple si elles vivent toujours dans l’automatisation du marketing), elles devront être transmises dans [!DNL Dynamics] et organisées dans les campagnes appropriées. Vous devrez ensuite tenir compte de la date du point de contact telle que vous souhaitez qu’elle reflète la date du passé, et non la date à laquelle vous l’avez poussée dans [!DNL Dynamics]. Pour remplacer cette date, vous pouvez utiliser le champ personnalisé « Date Buyer Touchpoint » pour modifier la date. Vous devez l’ajouter au formulaire Liste marketing.

![Si les données sont hébergées ailleurs (par exemple, si vous résidez toujours dans Marketing](assets/dynamics-lists-10.png)

Par conséquent, vous pouvez définir en masse la date pour chaque personne de cette liste marketing qui sera utilisée pour la date du point de contact. Pour obtenir des dates historiques plus précises, créez plusieurs listes marketing pour la même campagne, chacune ayant sa propre date de point de contact. Si la campagne a une courte durée, il serait peut-être utile de créer une liste marketing pour chaque jour. Si la campagne dure plus longtemps, il peut être judicieux de créer une liste marketing toutes les semaines.

Vous trouverez plus d’informations sur la synchronisation des listes marketing ici : [[!DNL Dynamics] Campagnes et listes marketing](/help/channel-tracking-and-setup/dynamics-campaigns-and-marketing-lists.md)

>[!NOTE]
>
>Si, pour une raison quelconque, une activité en ligne de suivi de campagne est active après la date d’activation de JavaScript, veillez à définir le champ « [!UICONTROL Date de fin du point de contact] » sur la date d’activation de JS. Cela permet d’éviter d’avoir des points de contact en double pour la même interaction.

Considérations : les données en ligne ajoutées de cette manière seront intrinsèquement moins granulaires que les données en ligne suivies [!DNL Marketo Measure] JavaScript. Par exemple, les champs tels que : URL du formulaire, Page de destination, Page du référent, etc., ne seront pas renseignés. Par conséquent, il est recommandé de répartir les campagnes dans chaque source si possible. Voici un exemple de mappage idéal.

| Type de campagne Dynamics | Canal | Sous-canal |
|---|---|---|
| Recherche payante - AdWords | Recherche payante | AdWords |
| Référencement Payant - Bing | Recherche payante | Bing |
| Référencement Payant - Yahoo | Recherche payante | Yahoo |

Si vous ne disposez pas d’un moyen d’identifier une source ou si cela ne vaut pas la peine, vous pouvez utiliser un type de campagne mappé à un canal appelé par exemple « Legacy Digital » ou « Historic Website ».

**Hors ligne:**

Pour que les efforts de marketing hors ligne aient des points de contact du passé, les données doivent être organisées en campagnes [!DNL Dynamics] et synchronisées avec les [!DNL Marketo Measure]. Le processus est le même que pour les canaux hors ligne actuels (synchroniser la campagne à l’aide de listes marketing ou de réponses de campagne). Vous trouverez ci-dessous un exemple de mappage de canal.

| Type de campagne Dynamics | Canal | Sous-canal |
|---|---|---|
| Événements - Conférences sponsorisées | Événements | Conférences sponsorisées |
| Événements - Événements de partenaire | Événements | Événements partenaires |
| Événements - Événements hébergés | Événements | Événements hébergés |
| Webinaire - Webinaire Partenaire | Webinaire | Webinaire Partenaire |

Si ces données ne sont pas déjà organisées en campagnes avec les dates correctes définies, vous pouvez utiliser le champ « Date Buyer Touchpoint » pour refléter la date exacte de l’activité hors ligne dans le passé.

