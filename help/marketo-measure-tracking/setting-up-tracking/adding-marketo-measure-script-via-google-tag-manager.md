---
unique-page-id: 18874797
description: Ajouter un script  [!DNL Marketo Measure]  via  [!DNL Google Tag Manager]  -  [!DNL Marketo Measure]
title: Ajout d’un script  [!DNL Marketo Measure]  via  [!DNL Google Tag Manager]
exl-id: 539efb10-35cb-4146-8eea-728c3948a11e
feature: Tracking
source-git-commit: 9e672d0c568ee0b889461bb8ba6fc6333edf31ce
workflow-type: tm+mt
source-wordcount: '192'
ht-degree: 100%

---

# Ajout d’un script [!DNL Marketo Measure] via [!DNL Google Tag Manager] {#adding-marketo-measure-script-via-google-tag-manager}

Lors de l’installation du code JavaScript [!DNL Marketo Measure], nous vous recommandons vivement de [coder en dur le script](/help/marketo-measure-tracking/setting-up-tracking/adding-marketo-measure-script.md){target="_blank"} directement sur votre site. Cependant, si cela n’est pas possible, vous pouvez également utiliser [!DNL Google Tag Manager] (GTM) pour charger le JS [!DNL Marketo Measure]. Veuillez noter que le JS [!DNL Marketo Measure] chargé via GTM est sujet à de la latence. La latence entraîne un délai de chargement du script, ce qui peut entraîner l’échec d’environ 3 à 5 % de tous les envois de formulaire.

Si vous décidez d’ajouter votre script via GTM, définissez le script [!DNL Marketo Measure] sur la priorité la plus élevée dans l’ordre de déclenchement et assurez-vous qu’il n’y a pas de scripts synchrones devant la balise [!DNL Marketo Measure] afin de réduire les effets liés à la latence de GTM.

>[!NOTE]
>
>Consultez cet [article d’aide de Google](https://support.google.com/tagmanager/answer/2772421?hl=fr){target="_blank"} pour en savoir plus.

## Comment ajouter un JS [!DNL Marketo Measure] via [!DNL Google Tag Manager] {#how-to-add-marketo-measure-js-via-google-tag-manager}

1. Ouvrez GTM et ajoutez le script [!DNL Marketo Measure] sur le conteneur de votre site web. Veillez à sélectionner **[!UICONTROL Balise HTML personnalisée]**.

1. Utilisez le script [!DNL Marketo Measure] ci-dessous et incorporez-le dans votre conteneur.

   `<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>`

1. Cliquez sur **[!UICONTROL Ajouter une règle de déclenchement]** pour indiquer à Google de charger notre fragment de code sur *toutes les pages*.

1. Accédez à la section Vue d’ensemble du brouillon de conteneur à gauche. Cliquez sur le bouton pour créer une version de votre conteneur et publier les modifications.
