---
unique-page-id: 18874600
description: Synchronisation des campagnes hors ligne - [!DNL Marketo Measure]
title: Synchronisation des campagnes hors ligne
exl-id: a6f9e217-ff6e-474d-9f14-c6f6238c9e84
feature: Channels
source-git-commit: b84909fbb34a1d8f739ebeea3400ef8816e17d32
workflow-type: tm+mt
source-wordcount: '722'
ht-degree: 6%

---

# Synchronisation des campagnes hors ligne {#syncing-offline-campaigns}

Il peut s’avérer difficile d’effectuer un suivi précis des campagnes hors ligne et de comparer ces campagnes à vos efforts de marketing numérique. [!DNL Marketo Measure] vous permet de suivre et d’attribuer des points de contact à vos campagnes hors ligne dans [!DNL Salesforce], même dans les situations où une campagne [!DNL Salesforce] n’est pas créée avant quelques semaines après l’événement.

>[!NOTE]
>
>Cet article traite d’un processus obsolète. Nous encourageons les utilisateurs et les utilisatrices à utiliser le [nouveau processus in-app amélioré](/help/channel-tracking-and-setup/offline-channels/custom-campaign-sync.md){target="_blank"}.

## Avant la synchronisation {#before-you-sync}

Voici quelques conseils pour un processus de synchronisation efficace :

* Les campagnes hors ligne font référence à des interactions marketing qui ne se produisent pas en ligne. Il s’agit notamment des canaux marketing tels que les événements, les webinaires et les dépannages. Incluez uniquement les campagnes marketing hors ligne.
* Si vous souhaitez inclure des campagnes qui ont suivi l’activité en ligne avant le moment où vous avez installé [!DNL Marketo Measure], veillez à définir la date de fin du point de contact comme date de déploiement de JavaScript sur votre site.
* Il est utile de garder l’application [!DNL Marketo Measure] ouverte sur la page Canaux hors ligne afin qu’il soit facile d’identifier les différents types de campagne, ainsi que le canal marketing dans lequel les points de contact seront regroupés.

* Vérifiez deux fois tout avant d&#39;appuyer sur le bouton &quot;[!UICONTROL Enregistrer]&quot; !

## Date de mise à jour en bloc du point de contact {#bulk-update-touchpoint-date}

Dans [!DNL Salesforce], le champ Date de création de l’objet membre de campagne indique la date à laquelle le membre de campagne a été ajouté à la campagne. Pour que le processus de synchronisation se déroule sans problème, assurez-vous que le champ Date Buyer Touchpoint a la même date que la date sur l’objet membre de campagne Salesforce. Cette étape est effectuée à l’aide du bouton &quot;[!UICONTROL Bulk Update Touchpoint Date]&quot;, _avant_ vous sélectionnez l’option [!UICONTROL picklist] dans le champ Activer les points de contact d’achat .

Pourquoi est-ce important ? Imaginez un instant que votre société sponsorise un stand lors d&#39;une conférence en janvier. Lors de la conférence, 100 personnes se sont montrées intéressées par votre produit et ont fourni leurs coordonnées pour recevoir des mises à jour par e-mail. Trois semaines plus tard, vous avez finalement créé une campagne dans [!DNL Salesforce] pour suivre le résultat de la conférence.

La date de téléchargement est fixée à trois semaines après celle de la conférence. Pour corriger cette différence, le bouton [!UICONTROL Bulk Update Touchpoint Date] peut être utilisé pour définir la date appropriée. Le bouton est illustré dans l’image ci-dessous.

![](assets/1-3.png)

Dans ce cas, la date de transfert serait renvoyée de trois semaines. Cette étape doit être effectuée avant de définir le champ &quot;[!UICONTROL Activer les points de contact d’achat]&quot;.

En résumé, si vous utilisez le bouton [!UICONTROL Mise à jour en bloc de la date de point de contact] et modifiez la date du point de contact par rapport à la date de l’événement, [!DNL Marketo Measure] générera des points de contact pour la date réelle de l’événement, et non la date du téléchargement.

Vous pouvez également mettre à jour les dates de tous les membres d’une campagne existante. Pour ce faire, veillez à ce que la date du point de contact soit la date de l’interaction du membre. Cliquez sur Mise à jour en bloc de la date Buyer Touchpoint, filtrez la liste des membres de campagne selon le cas, puis, dans l’option &quot;[!UICONTROL Sélectionner la date]&quot; au-dessus de la liste des membres de campagne, ajoutez la même date que la date à laquelle l’événement a eu lieu.

>[!CAUTION]
>
>Veillez à mettre à jour la date du point de contact _avant_ pour activer les points de contact pour tous les membres de la campagne.

![](assets/2-3.png)

## Comment créer une campagne et synchroniser les points de contact des acheteurs {#how-to-create-a-campaign-and-sync-buyer-touchpoints}

Pour créer une campagne dans [!DNL Salesforce], accédez à l’onglet [!UICONTROL Campagnes] et sélectionnez &quot;[!UICONTROL Nouveau]&quot; comme illustré dans l’image ci-dessous. Selon votre configuration [!DNL Salesforce], vous devrez peut-être ajouter des campagnes à la barre supérieure en cliquant sur l’icône plus (+).

![](assets/3-3.png)

Lors de la création de cette campagne, cliquez sur le champ &quot;[!UICONTROL Activer les points de contact d’achat]&quot; et sélectionnez l’une des options suivantes dans la liste de sélection :

![](assets/4-3.png)

* **Inclure tous les membres de campagne**
   * Cette option permet à [!DNL Marketo Measure] d’attribuer un point de contact à chaque membre de la campagne.

* **Inclure les membres de campagne &quot;réactifs&quot;.**
   * Cette option applique les points de contact aux membres de la campagne ayant le statut &quot;En réponse&quot;.

* **Exclure tous les membres de campagne.**
   * Cette option n’attribue aucun point de contact aux membres de la campagne et agit comme un indicateur que la campagne a été délibérément exclue de [!DNL Marketo Measure]. Si vous synchronisez par hasard une campagne avec les points de contact de l’utilisateur, vous pouvez modifier le statut en &quot;Exclure tous les membres de la campagne&quot; et les points de contact seront supprimés.

Une fois l’une de ces sélections sélectionnée, [!DNL Marketo Measure] attribuera à chaque membre de la campagne un point de contact, le cas échéant. Le prospect ou le contact ajouté à la campagne _must_ est associé à son enregistrement par une adresse électronique afin que [!DNL Marketo Measure] puisse créer un point de contact. Sans adresse e-mail, [!DNL Marketo Measure] n’attribuera pas de point de contact à la personne membre de la campagne.

>[!MORELIKETHIS]
>
>[[!DNL Marketo Measure] Tutoriels : mappage de canaux hors ligne](https://experienceleague.adobe.com/fr/docs/marketo-measure-learn/tutorials/onboarding/marketo-measure-salesforce/mapping-offline-channels){target="_blank"}
>
>[[!DNL Marketo Measure] Tutoriels : champs d’objets de campagne](https://experienceleague.adobe.com/fr/docs/marketo-measure-learn/tutorials/onboarding/marketo-measure-salesforce/campaign-object-fields){target="_blank"}
