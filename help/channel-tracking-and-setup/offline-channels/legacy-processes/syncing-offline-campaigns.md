---
description: Synchronisation des campagnes hors ligne - [!DNL Marketo Measure]
title: Synchronisation des campagnes hors ligne
exl-id: a6f9e217-ff6e-474d-9f14-c6f6238c9e84
feature: Channels
source-git-commit: c6090ce0c3ac60cd68b1057c369ce0b3b20aeeee
workflow-type: tm+mt
source-wordcount: '726'
ht-degree: 5%

---


# Synchronisation des campagnes hors ligne {#syncing-offline-campaigns}

Il peut être difficile d’effectuer un suivi précis des campagnes hors ligne et de comprendre comment elles se comparent à vos efforts de marketing numérique. [!DNL Marketo Measure] vous permet de suivre et d’attribuer des points de contact à vos campagnes hors ligne dans [!DNL Salesforce], même dans les cas où une campagne [!DNL Salesforce] n’est créée que quelques semaines après l’événement.

>[!NOTE]
>Cet article traite d’un processus obsolète. Nous encourageons les utilisateurs et les utilisatrices à utiliser le [nouveau processus in-app amélioré](/help/channel-tracking-and-setup/offline-channels/custom-campaign-sync.md){target="_blank"}.

## Avant la synchronisation {#before-you-sync}

Voici quelques conseils pour un processus de synchronisation efficace :

* Les campagnes hors ligne font référence aux interactions marketing qui ne se produisent pas en ligne. Il s’agit notamment des canaux marketing tels que les événements, les webinaires et les salons professionnels. N’incluez que les campagnes marketing hors ligne.
* Si vous souhaitez inclure des campagnes qui suivaient l’activité en ligne avant le moment de l’installation de [!DNL Marketo Measure], veillez à définir la Date de fin du point de contact sur la date à laquelle notre JavaScript a été déployé sur votre site.
* Il est utile de conserver l’application [!DNL Marketo Measure] ouverte sur la page Canaux hors ligne afin qu’il soit facile d’identifier les différents types de campagne, ainsi que le canal marketing dans lequel les points de contact seront regroupés.

* Vérifiez bien tout avant de cliquer sur le bouton « [!UICONTROL Enregistrer] » !

## Date de mise à jour en bloc du point de contact {#bulk-update-touchpoint-date}

Dans [!DNL Salesforce], le champ Date de création de l’objet Membre de la campagne indique la date à laquelle le membre de la campagne a été ajouté à la campagne. Pour que le processus de synchronisation se déroule sans problème, assurez-vous que le champ de date Buyer Touchpoint comporte la même date que celle de l’objet membre de la campagne Salesforce. Cette étape est effectuée à l&#39;aide du « [!UICONTROL Bouton de date de mise à jour en bloc des points de contact] » _avant_ de sélectionner l&#39;option [!UICONTROL liste de sélection] dans le champ Activer les points de contact de l&#39;acheteur.

Pourquoi est-ce important ? Imaginez un instant que votre entreprise ait commandité un kiosque lors d&#39;une conférence en janvier. Lors de la conférence, 100 personnes ont montré leur intérêt pour votre produit et ont fourni leurs coordonnées pour recevoir des mises à jour par e-mail. Trois semaines plus tard, vous avez finalement créé une campagne en [!DNL Salesforce] pour suivre les résultats de la conférence.

Votre date de chargement serait trois semaines plus tard que la date de la conférence. Pour corriger cette différence, le bouton [!UICONTROL Date de point de contact de mise à jour en bloc] peut être utilisé pour définir la date appropriée. Le bouton est illustré dans l’image ci-dessous.

![&#x200B; 3](assets/1-3.png)

Dans ce cas, la date de chargement est renvoyée de trois semaines. Cette étape doit être effectuée avant de définir le champ « [!UICONTROL &#x200B; Activer les points de contact de l’acheteur &#x200B;] ».

En résumé, si vous utilisez le bouton [!UICONTROL Mettre à jour en bloc la date de point de contact] et modifiez la date de point de contact en fonction de la date de l’événement, [!DNL Marketo Measure] générerez des points de contact pour la date réelle de l’événement, et non pour la date du chargement.

Vous pouvez également mettre à jour les dates de tous les membres d’une campagne existante. Lorsque vous procédez de la sorte, assurez-vous que la date du point de contact correspond à la date de l’interaction du membre. Cliquez sur le bouton Mettre à jour la date Buyer Touchpoint en bloc, filtrez la liste des membres de la campagne selon vos besoins et, dans l’option « [!UICONTROL &#x200B; Sélectionner la date &#x200B;] » au-dessus de la liste des membres de la campagne, ajoutez la même date que la date à laquelle l’événement a eu lieu.

>[!CAUTION]
>Veillez à mettre à jour la date du point de contact _avant_ vous activez les points de contact pour tous les membres de la campagne.

![&#x200B; 3](assets/2-3.png)

## Création d’une campagne et synchronisation des points de contact d’acheteur {#how-to-create-a-campaign-and-sync-buyer-touchpoints}

Pour créer une campagne dans [!DNL Salesforce], accédez à l’onglet [!UICONTROL Campagnes] et sélectionnez « [!UICONTROL Nouveau] » comme illustré dans l’image ci-dessous. Selon la configuration de votre [!DNL Salesforce], vous devrez peut-être ajouter des campagnes à la barre supérieure en cliquant sur l’icône plus (+).

![&#x200B; 3](assets/3-3.png)

Lorsque vous créez cette campagne, cliquez sur le champ « [!UICONTROL &#x200B; Activer les points de contact de l’acheteur &#x200B;] » et sélectionnez l’une des options suivantes dans la liste de sélection :

![&#x200B; 3](assets/4-3.png)

* **Inclure tous les membres de la campagne**
   * Cette option [!DNL Marketo Measure] permet d’attribuer un point de contact à chaque membre de la campagne.

* **Incluez les membres de la campagne « Répondus ».**
   * Cette option applique les points de contact aux membres de la campagne qui ont un statut « Répondu ».

* **Exclure tous les membres de la campagne.**
   * Cette option n’attribue de points de contact à aucun membre de la campagne et agit comme un indicateur du fait que la campagne a été délibérément exclue de la [!DNL Marketo Measure]. Si vous synchronisez une campagne avec les points de contact de l’acheteur par accident, vous pouvez modifier le statut en « Exclure tous les membres de la campagne » et les points de contact seront supprimés.

Une fois l’une de ces sélections choisie, [!DNL Marketo Measure] attribuerez un point de contact à chaque membre de la campagne, le cas échéant. Le prospect ou le contact ajouté à la campagne _doit_ disposer d’une adresse e-mail associée à son enregistrement pour que [!DNL Marketo Measure] puissiez créer un point de contact. Sans adresse e-mail, [!DNL Marketo Measure] n’attribuera pas de point de contact à la personne membre de la campagne.

>[!MORELIKETHIS]
>[[!DNL Marketo Measure] Tutoriels : Mappage de canaux hors ligne](https://experienceleague.adobe.com/fr/docs/marketo-measure-learn/tutorials/onboarding/marketo-measure-salesforce/mapping-offline-channels){target="_blank"}
>[[!DNL Marketo Measure] Tutoriels : Champs D’Objet De Campagne](https://experienceleague.adobe.com/fr/docs/marketo-measure-learn/tutorials/onboarding/marketo-measure-salesforce/campaign-object-fields){target="_blank"}
