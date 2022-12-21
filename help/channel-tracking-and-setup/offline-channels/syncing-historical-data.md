---
unique-page-id: 42762310
description: Synchronisation des données historiques - [!DNL Marketo Measure] - Documentation du produit
title: Synchronisation des données historiques
exl-id: 5a3c1a71-463a-4d75-98b9-fc225839512a
source-git-commit: 02f686645e942089df92800d8d14c76215ae558f
workflow-type: tm+mt
source-wordcount: '1496'
ht-degree: 2%

---

# Synchronisation des données historiques {#syncing-historical-data}

[!DNL Marketo Measure] est une solution qui fournit les données les plus granulaires et exploitables. Nous comprenons toutefois que vous souhaitez peut-être avoir des données existantes pour lesquelles vous souhaitez obtenir une attribution. Il est possible de générer des points de contact pour les données historiques, mais il est important de prendre en compte quelques facteurs avant de poursuivre ce processus.

## Facteurs à prendre en compte {#factors-to-consider}

**Les données sont-elles déjà organisées en campagnes ?**

a. Les données doivent être organisées en campagnes pour être synchronisées avec [!DNL Marketo Measure] afin que les points de contact soient générés. S’il n’est pas actuellement organisé en campagnes, vous voudrez déterminer s’il vaut le temps et les ressources nécessaires pour segmenter les données dans les campagnes appropriées.

b. La date à laquelle le membre a été ajouté à la campagne ou marquée comme ayant répondu sera utilisée pour la date du point de contact. Par conséquent, cette information doit également être exacte. [!DNL Marketo Measure] propose des solutions de contournement à la fois dans la collecte de données régionale et dans le document de base de données pour mettre à jour les dates, mais cela peut prendre du temps en fonction du volume.

**Disposez-vous d’une quantité assez égale de données organisées en campagnes pour tous les canaux (référencement payant, événements, organiques, etc.) ?**

Il est important d’avoir une image équilibrée de l’attribution afin d’avoir des rapports précis et &quot;justes&quot;. Par exemple, si vous ne disposez que de données pour les efforts de canal hors ligne historiques tels que les événements, les données seront intrinsèquement biaisées sans données en ligne historiques pour les compléter.

**Quel niveau de granularité attendez-vous ?**

Vous ne connaissez que le nom du canal, du sous-canal et de la campagne.

**Quels sont vos objectifs en matière de création de rapports à l’avenir ?**

Ces données vont être limitées. Il est donc important de réfléchir à la façon dont vous envisagez de les utiliser. Il n’est peut-être pas plus judicieux de comparer les données historiques aux données futures.

**Jusqu&#39;où voulez-vous retourner ?**

[!DNL Marketo Measure] recommande vivement de ne pas dépasser l’année précédente.

Il s’agit d’un sujet que nous vous encourageons vivement à discuter avec votre [!DNL Marketo Measure] contactez d&#39;abord. Si vous avez pris en compte les points ci-dessus et que vous souhaitez poursuivre, les instructions générales (séparées par [!DNL Salesforce] et [!DNL Microsoft Dynamics]) sont ci-dessous.

## Synchronisation des campagnes historiques dans [!DNL Salesforce] {#syncing-historic-campaigns-in-salesforce}

**En ligne :**

Pour synchroniser les données en ligne historiques, les données doivent être organisées en campagnes Salesforce vers lesquelles vous pouvez ensuite vous synchroniser. [!DNL Marketo Measure] via [!DNL Salesforce] Règles de synchronisation de campagne dans [!DNL Marketo Measure] application. Il est important de s’assurer que les points de contact ne sont générés à partir d’aucune de ces campagnes une fois la date d’activation de votre code JavaScript terminée. Cela permet d’éviter les points de contact en double. Une fois le code JavaScript actif, les efforts en ligne sont automatiquement suivis. Nous ne voulons donc pas les suivre également via une campagne SFDC. Pour éviter ce problème, veillez à ajouter un sentiment de temps à la règle. Peut-être que &quot;La date de création du membre de campagne est inférieure à [Date d’activation JavaScript]&quot;.

![](assets/syncing-historical-data-1.png)

Le composant de mappage des canaux pour les données en ligne historiques peut être un peu délicat. Nous voulons qu’il corresponde autant que possible à vos règles de canal en ligne actuelles (à partir de la feuille de règles en ligne) pour des rapports propres. Vous trouverez ci-dessous un exemple de mappage de canal idéal.

>[!NOTE]
>
>Ce mappage de canal est effectué dans la variable [!UICONTROL Canaux hors ligne] de la section [!DNL Marketo Measure] car nous utilisons des campagnes SFDC.

| Type de campagne Salesforce | Canal | Sous-canal |
|---|---|---|
| Recherche payante - AdWords | Référencement payant | AdWords |
| Recherche payante - Bing | Référencement payant | Bing |
| Recherche payante - Yahoo | Référencement payant | Yahoo |

Les données en ligne ainsi ajoutées seront par nature moins granulaires que les données en ligne [!DNL Marketo Measure] effectue un suivi via JavaScript. Par exemple, les champs tels que URL du formulaire, Landing Page, Referrer Page, etc. ne seront pas renseignés. Par conséquent, il est recommandé de ventiler les campagnes dans chaque source si possible. Comme nous l’avons vu dans l’exemple ci-dessus, vous devez disposer de plusieurs types de campagne pour chaque source afin de disposer de la granularité dans les rapports.

Il peut ne pas être possible ou raisonnable d’avoir le nombre de types de campagne SFDC pour prendre en charge le mappage granulaire des canaux. Vous pouvez donc vous contenter de mapper au niveau du canal et ignorer les sous-canaux. Si le niveau du canal n’est pas connu non plus, vous pouvez configurer un canal proxy tel que &quot;Numérique historique&quot; afin que vous sachiez au moins qu’il s’agissait d’une touche en ligne.

Si vous devez modifier en masse la date du point de contact qui sera transmise pour ces efforts historiques en ligne, utilisez la variable [!DNL Marketo Measure] custom &quot;[!UICONTROL Date de point de contact de mise à jour en bloc]&quot; (ce champ est disponible sous la forme d’un champ personnalisé dans l’objet Campaign de la collecte de données régionale). Si la campagne a une courte période, il serait peut-être utile de modifier en masse la date du point de contact un jour par intervalle de jour, tandis qu’il serait logique de mettre à jour en masse une fois par semaine si la campagne a une période plus longue. Si vous utilisez la fonctionnalité de mise à jour en bloc de date de point de contact, veillez à mettre à jour la règle de synchronisation de campagne afin d’utiliser la date du point de contact de l’acheteur dans le champ de date. Notez que cela peut nécessiter d’être créatif avec vos règles de synchronisation de campagne si cela ne s’applique qu’à une ou deux campagnes et pas à toutes.

**Hors ligne:**

Les données historiques des efforts de marketing hors ligne (celles qui ne peuvent pas être suivies via JavaScript) devront également être organisées en campagnes SFDC. Les campagnes SFDC sont la voie [!DNL Marketo Measure] effectue le suivi des efforts hors ligne, que l’activité soit &quot;historique&quot; ou &quot;actuelle/post-&quot;.[!DNL Marketo Measure] &quot;mise en oeuvre&quot;, veuillez suivre le même mappage de canal que celui décidé lors de la formation initiale sur la configuration des canaux hors ligne.

Si nécessaire, utilisez le bouton &quot;Mise à jour en masse de la date du point de contact&quot; pour modifier en masse la date du point de contact pour les membres de la campagne. Par exemple, si vous créez des campagnes SFDC après que l’événement s’est produit, vous souhaitez effectuer des modifications en masse pour la date correcte. Si vous utilisez la fonctionnalité de mise à jour en bloc de date de point de contact, veillez à mettre à jour la règle de synchronisation de campagne afin d’utiliser la date du point de contact de l’acheteur dans le champ de date. Notez que cela peut nécessiter d’être créatif avec vos règles de synchronisation de campagne si cela ne s’applique qu’à une ou deux campagnes et pas à toutes.

## Synchronisation des campagnes historiques dans [!DNL Dynamics] {#syncing-historic-campaigns-in-dynamics}

[!DNL Marketo Measure] peut générer rétroactivement des points de contact pour les interactions qui se sont produites dans le passé, à condition qu’ils soient organisés en campagnes dans [!DNL Dynamics].

Cela implique généralement de travailler dans le CRM pour tenir compte des dates historiques. La gestion sera également différente pour les efforts en ligne (suivis par JS) et les efforts hors ligne (qui ne peuvent pas être suivis par JS).

Suivez les instructions ci-dessous pour organiser les données historiques dans [!DNL Dynamics] dans un format pouvant être synchronisé avec [!DNL Marketo Measure].

**En ligne :**

Les données numériques historiques doivent être organisées en [!DNL Dynamics] campagnes afin d’être renvoyées. Idéalement, cette structure est déjà en place.

Si les données sont hébergées ailleurs (comme toujours dans l’automatisation du marketing), elles doivent être transmises à [!DNL Dynamics] et organisées en campagnes appropriées. Vous devrez ensuite prendre en compte la date du point de contact, car vous souhaitez qu’elle reflète la date du passé, et non la date à laquelle vous l’avez envoyée. [!DNL Dynamics]. Pour remplacer cette date, vous pouvez utiliser le champ personnalisé &quot;Date du point de contact de l’acheteur&quot; pour modifier la date. Vous devez l’ajouter au formulaire Liste marketing.

![](assets/syncing-historical-data-2.png)

Par conséquent, vous pouvez définir en masse la date pour chaque personne de cette liste marketing qui sera utilisée pour la date du point de contact. Pour obtenir des dates historiques plus précises, créez plusieurs listes marketing pour la même campagne, chacune ayant sa propre date de point de contact. Si la campagne a une courte période, il serait peut-être utile de créer une liste marketing pour chaque jour. Si la durée de la campagne est plus longue, il peut être logique de créer une liste marketing sur une base hebdomadaire.

Vous trouverez plus d’informations sur la synchronisation des listes marketing ici : [[!DNL Dynamics] Campagnes et listes marketing](/help/marketo-measure-and-dynamics/dynamics-reporting/dynamics-campaigns-and-marketing-lists.md)

>[!NOTE]
>
>Si, pour une raison quelconque, vous disposez d’une activité de suivi de campagne en ligne principale au-delà de la date d’activation de JavaScript, veillez à définir le paramètre &quot;&quot;[!UICONTROL Date de fin du point de contact]&quot; à la date d’activation du JS. Cela permet d’éviter la duplication des points de contact pour une même interaction.

Considérations : Les données en ligne ainsi ajoutées seront par nature moins granulaires que les données en ligne [!DNL Marketo Measure] effectue un suivi via JavaScript. Par exemple, des champs tels que : L’URL du formulaire, la page d’entrée, la page du référent, etc., ne seront pas renseignées. Par conséquent, il est recommandé de ventiler les campagnes dans chaque source si possible. Vous trouverez ci-dessous un exemple de mappage idéal.

| Type de campagne Dynamics | Canal | Sous-canal |
|---|---|---|
| Recherche payante - AdWords | Référencement payant | AdWords |
| Recherche payante - Bing | Référencement payant | Bing |
| Recherche payante - Yahoo | Référencement payant | Yahoo |

Si vous n’avez pas de moyen d’identifier une source ou si elle ne vaut pas le temps et les efforts, vous pouvez utiliser un type de campagne mappé à un canal appelé &quot;Legacy Digital&quot; ou &quot;History Website.

**Hors ligne:**

Pour disposer de points de contact pour les efforts de marketing hors ligne du passé, les données doivent être organisées en [!DNL Dynamics] campagnes et synchronisées avec [!DNL Marketo Measure]. Le processus est le même que pour les canaux hors ligne actuels (synchronisation de la campagne via les listes marketing ou les réponses de campagne). Vous trouverez ci-dessous un exemple de mappage des canaux.

| Type de campagne Dynamics | Canal | Sous-canal |
|---|---|---|
| Événements - Conférences sponsorisées | Événements | Conférences parrainées |
| Événements - Événements de partenaire | Événements | Événements de partenaire |
| Événements - Événements hébergés | Événements | Événements hébergés |
| Webinaire - Webinaire partenaire | Webinaire | Webinaire du partenaire |

Si ces données ne sont pas déjà organisées en campagnes avec les dates correctes définies, vous pouvez utiliser le champ &quot;Date du point de contact de l’acheteur&quot; pour refléter la date exacte de l’activité hors ligne dans le passé.

