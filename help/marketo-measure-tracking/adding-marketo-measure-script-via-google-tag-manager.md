---
description: Ajout  [!DNL Marketo Measure]  script via [!DNL Google Tag Manager] guidance pour les utilisateurs Marketo Measure
title: Ajout d’un script  [!DNL Marketo Measure]  via  [!DNL Google Tag Manager]
exl-id: 539efb10-35cb-4146-8eea-728c3948a11e
feature: Tracking
hidefromtoc: true
source-git-commit: 0299ef68139df574bd1571a749baf1380a84319b
workflow-type: tm+mt
source-wordcount: '197'
ht-degree: 83%

---

# Ajout d’un script [!DNL Marketo Measure] via [!DNL Google Tag Manager] {#adding-marketo-measure-script-via-google-tag-manager}

Lors de l’installation de [!DNL Marketo Measure] JavaScript, il est recommandé de [coder le script en dur](/help/marketo-measure-tracking/adding-marketo-measure-script.md){target="_blank"} directement sur le site. Cependant, si cela n’est pas possible, vous pouvez également utiliser [!DNL Google Tag Manager] (GTM) pour charger le JS [!DNL Marketo Measure]. Veuillez noter que le JS [!DNL Marketo Measure] chargé via GTM est sujet à de la latence. La latence entraîne un délai de chargement du script, ce qui peut entraîner l’échec d’environ 3 à 5 % de tous les envois de formulaire.

Si vous décidez d’ajouter votre script via GTM, définissez le script [!DNL Marketo Measure] sur la priorité la plus élevée dans l’ordre de déclenchement et assurez-vous qu’il n’y a pas de scripts synchrones devant la balise [!DNL Marketo Measure] afin de réduire les effets liés à la latence de GTM.

>[!NOTE]
>
>Pour en savoir plus, consultez cet article d[assistance de Google](https://support.google.com/tagmanager/answer/2772421?hl=fr){target="_blank"}.

## Comment ajouter un JS [!DNL Marketo Measure] via [!DNL Google Tag Manager] {#how-to-add-marketo-measure-js-via-google-tag-manager}

1. Ouvrez GTM et ajoutez le script [!DNL Marketo Measure] sur le conteneur de votre site web. Veillez à sélectionner **[!UICONTROL Balise HTML personnalisée]**.

1. Utilisez le script [!DNL Marketo Measure] ci-dessous et incorporez-le dans votre conteneur.

   `<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>`

1. Cliquez sur **[!UICONTROL Ajouter une règle de déclenchement]** pour indiquer à Google de charger notre fragment de code sur *toutes les pages*.

1. Accédez à la section Vue d’ensemble du brouillon de conteneur à gauche. Cliquez sur le bouton pour créer une version de votre conteneur et publier les modifications.
