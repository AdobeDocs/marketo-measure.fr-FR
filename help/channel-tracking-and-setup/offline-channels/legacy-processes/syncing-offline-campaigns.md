---
unique-page-id: 18874600
description: Synchronisation des campagnes hors ligne - [!DNL Marketo Measure]
title: Synchronisation des campagnes hors ligne
exl-id: a6f9e217-ff6e-474d-9f14-c6f6238c9e84
feature: Channels
source-git-commit: 4787f765348da71bc149c997470ce678ba498772
workflow-type: tm+mt
source-wordcount: '722'
ht-degree: 0%

---

# Synchronisation des campagnes hors ligne {#syncing-offline-campaigns}

Il peut s’avérer difficile d’effectuer un suivi précis des campagnes hors ligne et de comparer ces campagnes à vos efforts de marketing numérique. [!DNL Marketo Measure] vous permet de suivre et d’attribuer des points de contact à vos campagnes hors ligne dans [!DNL Salesforce], même dans les cas où une [!DNL Salesforce] La campagne n’est créée que quelques semaines après l’événement.

>[!NOTE]
>
>Cet article couvre un processus obsolète. Nous encourageons les utilisateurs à utiliser la variable [nouveau processus in-app amélioré](/help/channel-tracking-and-setup/offline-channels/custom-campaign-sync.md){target="_blank"}.

## Avant la synchronisation {#before-you-sync}

Voici quelques conseils pour un processus de synchronisation efficace :

* Les campagnes hors ligne font référence à des interactions marketing qui ne se produisent pas en ligne. Il s’agit notamment des canaux marketing tels que les événements, les webinaires et les dépannages. Incluez uniquement les campagnes marketing hors ligne.
* Si vous souhaitez inclure des campagnes qui ont suivi l’activité en ligne avant l’installation [!DNL Marketo Measure], veillez à définir la date de fin du point de contact comme date de déploiement de votre code JavaScript sur votre site.
* Il est utile de conserver la variable [!DNL Marketo Measure] L’application s’ouvre sur la page Canaux hors ligne afin qu’il soit facile d’identifier les différents types de campagne, ainsi que le canal marketing dans lequel les points de contact seront regroupés.

* Vérifiez tous les éléments avant d’accéder au[!UICONTROL Enregistrer]&quot;.

## Date de point de contact de mise à jour en bloc {#bulk-update-touchpoint-date}

Dans [!DNL Salesforce], le champ Date de création de l’objet membre de campagne indique la date à laquelle le membre de campagne a été ajouté à la campagne. Pour que le processus de synchronisation se déroule sans problème, assurez-vous que le champ Date point de contact de l’acheteur a la même date que la date sur l’objet membre de campagne Salesforce. Cette étape est effectuée à l’aide du[!UICONTROL Bouton Mettre à jour la date du point de contact en bloc],&quot; _before_ vous sélectionnez la variable [!UICONTROL liste de sélection] dans le champ Activer les points de contact de l’acheteur .

Pourquoi est-ce important ? Imaginez un instant que votre société sponsorise un stand lors d&#39;une conférence en janvier. Lors de la conférence, 100 personnes se sont montrées intéressées par votre produit et ont fourni leurs coordonnées pour recevoir des mises à jour par e-mail. Trois semaines plus tard, vous avez finalement créé une campagne dans [!DNL Salesforce] pour suivre les résultats de la conférence.

La date de téléchargement est fixée à trois semaines après celle de la conférence. Pour corriger cette différence, la variable [!UICONTROL Date de point de contact de mise à jour en bloc] peut être utilisé pour définir la date appropriée. Le bouton est illustré dans l’image ci-dessous.

![](assets/1-3.png)

Dans ce cas, la date de transfert serait renvoyée de trois semaines. Cette étape doit être effectuée avant de définir le paramètre[!UICONTROL Activation des points de contact d’achat]&quot;.

En résumé, si vous utilisez la variable [!UICONTROL Date de point de contact de mise à jour en bloc] et modifiez la date du point de contact à la date de l’événement, [!DNL Marketo Measure] génère des points de contact pour la date réelle de l’événement, et non la date du téléchargement.

Vous pouvez également mettre à jour les dates de tous les membres d’une campagne existante. Pour ce faire, veillez à ce que la date du point de contact soit la date de l’interaction du membre. Cliquez sur la Date de point de contact de l’achat de mise à jour en bloc, filtrez la liste des membres de la campagne selon le cas et dans le[!UICONTROL Sélectionner la date]&quot; au-dessus de la liste des membres de la campagne, ajoutez la même date que celle à laquelle l&#39;événement a eu lieu.

>[!CAUTION]
>
>Veillez à mettre à jour la date du point de contact. _before_ vous activez Points de contact pour tous les membres de la campagne.

![](assets/2-3.png)

## Comment créer une campagne et synchroniser les points de contact des acheteurs {#how-to-create-a-campaign-and-sync-buyer-touchpoints}

Pour créer une campagne dans [!DNL Salesforce], accédez à la [!UICONTROL Campagnes] et sélectionnez &quot;[!UICONTROL Nouveau]&quot; comme illustré dans l’image ci-dessous. Selon votre [!DNL Salesforce] configuré, vous devrez peut-être ajouter des campagnes à la barre supérieure en cliquant sur l’icône plus (+).

![](assets/3-3.png)

Lorsque vous créez cette campagne, cliquez sur le bouton &quot;[!UICONTROL Activation des points de contact d’achat]&quot; et sélectionnez l’une des options suivantes dans la liste de sélection :

![](assets/4-3.png)

* **Inclure tous les membres de la campagne**
   * Cette option active [!DNL Marketo Measure] pour attribuer un point de contact à chaque membre de la campagne.

* **Inclure les membres de campagne &quot;réactifs&quot;.**
   * Cette option applique les points de contact aux membres de la campagne ayant le statut &quot;En réponse&quot;.

* **Exclure tous les membres de l&#39;opération.**
   * Cette option n’attribue aucun point de contact aux membres de la campagne et agit comme un indicateur dont la campagne a été délibérément exclue. [!DNL Marketo Measure]. Si vous synchronisez par hasard une campagne avec les points de contact de l’utilisateur, vous pouvez modifier le statut en &quot;Exclure tous les membres de la campagne&quot; et les points de contact seront supprimés.

Une fois l’une de ces sélections sélectionnée, [!DNL Marketo Measure] attribuera à chaque membre de la campagne un point de contact, le cas échéant. Le prospect ou le contact ajouté à la campagne _must_ avoir une adresse électronique associée à leur enregistrement pour [!DNL Marketo Measure] pour créer un point de contact. Sans adresse email, [!DNL Marketo Measure] n’affectera pas de point de contact au membre de la campagne.

>[!MORELIKETHIS]
>
>[[!DNL Marketo Measure] Université : mappage des canaux hors ligne](https://universityonline.marketo.com/courses/bizible-fundamentals-channel-management/#/page/5c630eca34d9f0367662b77f)
>
>[[!DNL Marketo Measure] Université : champs d’objet de campagne](https://universityonline.marketo.com/courses/bizible-fundamentals-channel-management/#/page/5c63007334d9f0367662b758)
