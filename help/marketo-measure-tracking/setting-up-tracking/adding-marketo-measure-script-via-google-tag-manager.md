---
unique-page-id: 18874797
description: Ajouter [!DNL Marketo Measure] Script via [!DNL Google Tag Manager] - [!DNL Marketo Measure]
title: Ajout d’un script  [!DNL Marketo Measure]  via  [!DNL Google Tag Manager]
exl-id: 539efb10-35cb-4146-8eea-728c3948a11e
feature: Tracking
source-git-commit: 9e672d0c568ee0b889461bb8ba6fc6333edf31ce
workflow-type: tm+mt
source-wordcount: '192'
ht-degree: 44%

---

# Ajout d’un script [!DNL Marketo Measure] via [!DNL Google Tag Manager] {#adding-marketo-measure-script-via-google-tag-manager}

Lors de l’installation du [!DNL Marketo Measure] JavaScript, il est recommandé de [codage dur du script](/help/marketo-measure-tracking/setting-up-tracking/adding-marketo-measure-script.md){target="_blank"} directement sur le site. Si cela n’est pas possible, vous pouvez également utiliser [!DNL Google Tag Manager] (GTM) pour charger la variable [!DNL Marketo Measure] JS. Notez que [!DNL Marketo Measure] Les fichiers JS chargés via GTM sont sensibles à la latence. La latence entraîne un délai de chargement du script, ce qui peut entraîner l’absence d’environ 3 à 5 % de tous les envois de formulaire.

Si vous décidez d’ajouter votre script via GTM, définissez la variable [!DNL Marketo Measure] de la priorité la plus élevée dans l’ordre de déclenchement et assurez-vous qu’il n’y a pas de scripts synchrones devant la balise [!DNL Marketo Measure] pour réduire les effets liés à la latence de GTM.

>[!NOTE]
>
>Utilisez cette [Article de prise en charge par Google](https://support.google.com/tagmanager/answer/2772421?hl=fr&amp;sjid=5438088820075065836-EU){target="_blank"} pour en savoir plus.

## Comment ajouter un JS [!DNL Marketo Measure] via [!DNL Google Tag Manager] {#how-to-add-marketo-measure-js-via-google-tag-manager}

1. Ouvrez GTM et ajoutez le script [!DNL Marketo Measure] sur le conteneur de votre site web. Veillez à sélectionner **[!UICONTROL Balise HTML personnalisée]**.

1. Utilisez le script [!DNL Marketo Measure] ci-dessous et incorporez-le dans votre conteneur.

   `<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>`

1. Cliquez sur **[!UICONTROL Ajouter une règle de déclenchement]** pour indiquer à Google de charger notre fragment de code sur *toutes les pages*.

1. Accédez à la section Vue d’ensemble du brouillon de conteneur à gauche. Cliquez sur le bouton pour créer une version de votre conteneur et publier les modifications.
