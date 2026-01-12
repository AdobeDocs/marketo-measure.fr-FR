---
description: Suppression des paramètres de suivi [!DNL Marketo Measure] de l’URL de la page de destination dans Google Analytics
title: Suppression des paramètres de suivi [!DNL Marketo Measure] de l’URL de la page de destination dans Google Analytics
exl-id: ec81ba4a-bb10-49fd-b62e-5a1bc9e1a023
feature: Tracking
source-git-commit: c6090ce0c3ac60cd68b1057c369ce0b3b20aeeee
workflow-type: tm+mt
source-wordcount: '115'
ht-degree: 19%

---


# Suppression des paramètres de suivi [!DNL Marketo Measure] de l’URL de la page de destination dans Google Analytics {#remove-marketo-measure-tracking-parameters-from-the-landing-page-url-in-google-analytics}

Parfois, lorsque vous affichez des pages de destination dans [!DNL Google Analytics], vous souhaiterez supprimer les paramètres de tracking des URL. Sinon, elles seront divisées en lignes individuelles.

Heureusement, c&#39;est une solution facile.

1. Dans [!DNL Google Analytics], accédez à [!UICONTROL Admin] >[!UICONTROL Afficher les paramètres] >[!UICONTROL Exclure les paramètres de requête d’URL].
1. Tapez « _bt,_bk,_bm,_bn,_bg » dans la zone (moins les guillemets).
1. Faites défiler vers le bas et cliquez sur **[!UICONTROL Enregistrer]**.

   Gardez à l’esprit que [!DNL Google Analytics] ne retraite pas les données. Par conséquent, cette modification ne sera reflétée qu’à l’avenir, et vos données antérieures s’afficheront toujours avec les paramètres bt, bk et bm.
