---
unique-page-id: 18874797
description: Ajout d’un script [!DNL Marketo Measure] via [!DNL Google Tag Manager] - [!DNL Marketo Measure]
title: Ajout d’un script [!DNL Marketo Measure] via [!DNL Google Tag Manager]
exl-id: 539efb10-35cb-4146-8eea-728c3948a11e
feature: Tracking
TQID: 'https://experienceleague.adobe.com/g3PTxiShipF9q79oIAWKZIUU-YFMarLEDeKknaPiHck'
product_v2:
  - id: e6fc4016-a972-4f36-8c30-a6a5f82ad0c8
    internal-label: Marketo Measure
feature_v2:
  - id: dcbeff6e-0253-5a4b-9ac2-1b67cc4a6286
    internal-label: Tracking
source-git-commit: 940fee4abd0e09b6bf513b5e7526d3c242bd31c7
workflow-type: tm+mt
source-wordcount: '199'
ht-degree: 93%
---
# Ajout d’un script [!DNL Marketo Measure] via [!DNL Google Tag Manager] {#adding-marketo-measure-script-via-google-tag-manager}

Lors de l’installation du code JavaScript [!DNL Marketo Measure], nous vous recommandons vivement de [coder en dur le script](/help/marketo-measure-tracking/setting-up-tracking/adding-marketo-measure-script.md){target="_blank"} directement sur votre site. Cependant, si cela n’est pas possible, vous pouvez également utiliser [!DNL Google Tag Manager] (GTM) pour charger le JS [!DNL Marketo Measure]. Veuillez noter que le JS [!DNL Marketo Measure] chargé via GTM est sujet à de la latence. La latence entraîne un délai de chargement du script, ce qui peut entraîner l’échec d’environ 3 à 5 % de tous les envois de formulaire.

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
