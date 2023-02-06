---
unique-page-id: 18874797
description: Ajouter [!DNL Marketo Measure] Script via [!DNL Google Tag Manager] - [!DNL Marketo Measure] - Documentation du produit
title: Ajouter [!DNL Marketo Measure] Script via [!DNL Google Tag Manager]
exl-id: 539efb10-35cb-4146-8eea-728c3948a11e
source-git-commit: 82cc8269bfdb26b6acf039d0ce0e06564f5e2612
workflow-type: tm+mt
source-wordcount: '200'
ht-degree: 0%

---

# Ajouter [!DNL Marketo Measure] Script via [!DNL Google Tag Manager] {#adding-marketo-measure-script-via-google-tag-manager}

Lors de l’installation du [!DNL Marketo Measure] javascript, nous vous recommandons vivement [codage dur du script](/help/marketo-measure-tracking/setting-up-tracking/adding-marketo-measure-script.md){target="_blank"} directement sur votre site. Cependant, si cela n’est pas possible, vous pouvez également utiliser [!DNL Google Tag Manager] (GTM) pour charger la variable [!DNL Marketo Measure] JS. Veuillez noter que [!DNL Marketo Measure] Les fichiers JS chargés via GTM sont sensibles à la latence. La latence entraîne un délai dans le temps de chargement du script, ce qui peut entraîner l’absence d’environ 3 à 5 % de tous les envois de formulaire.

Si vous décidez d’ajouter votre script via GTM, définissez la variable [!DNL Marketo Measure] de la priorité la plus élevée dans l’ordre de déclenchement et assurez-vous qu’il n’y a pas de scripts synchrones devant la balise [!DNL Marketo Measure] afin de réduire les effets liés à la latence de GTM.

>[!NOTE]
>
>Veuillez utiliser [Article de prise en charge par Google](https://support.google.com/tagmanager/answer/2772421?hl=en){target="_blank"} pour en savoir plus.

## Comment ajouter [!DNL Marketo Measure] JS via [!DNL Google Tag Manager] {#how-to-add-marketo-measure-js-via-google-tag-manager}

1. Ouvrez GTM et ajoutez le [!DNL Marketo Measure] sur le conteneur de votre site web. Veillez à sélectionner **[!UICONTROL Balise de HTML personnalisée]**.

1. Utilisez la variable [!DNL Marketo Measure] script ci-dessous et incorporez-le dans votre conteneur.

   `<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>`

1. Cliquez sur **[!UICONTROL Ajouter une règle de déclenchement]** afin que vous puissiez indiquer à Google de charger notre fragment de code *Toutes les pages*.

1. Accédez à la section Aperçu du brouillon de conteneur à gauche. Cliquez sur le bouton pour créer une version de votre conteneur et publier les modifications.
