---
unique-page-id: 18874736
description: Supprimer [!DNL Marketo Measure] Paramètres de suivi de l’URL de la page d’entrée en Google Analytics - [!DNL Marketo Measure]
title: Suppression des paramètres de suivi [!DNL Marketo Measure] de l’URL de la page de destination dans Google Analytics
exl-id: ec81ba4a-bb10-49fd-b62e-5a1bc9e1a023
feature: Tracking
source-git-commit: 915e9c5a968ffd9de713b4308cadb91768613fc5
workflow-type: tm+mt
source-wordcount: '115'
ht-degree: 9%

---

# Supprimer [!DNL Marketo Measure] Paramètres de suivi à partir de l’URL de la page d’entrée en Google Analytics {#remove-marketo-measure-tracking-parameters-from-the-landing-page-url-in-google-analytics}

Parfois lors de l’affichage de landing pages dans [!DNL Google Analytics], vous souhaitez supprimer les paramètres de suivi des URL. Sinon, elles seront divisées en lignes individuelles.

Heureusement, c&#39;est une solution facile.

1. Dans [!DNL Google Analytics], accédez à [!UICONTROL Administration] >[!UICONTROL Paramètres d’affichage] >[!UICONTROL Exclure les paramètres de requête d’URL].
1. Saisissez &quot;_bt,_bk,_bm,_bn,_bg&quot; dans la zone (sans les guillemets).
1. Faites défiler la page vers le bas et cliquez sur **[!UICONTROL Enregistrer]**.

   N’oubliez pas que [!DNL Google Analytics] ne retraite pas les données. Par conséquent, cette modification ne sera reflétée que par la suite, et vos données antérieures s’afficheront toujours avec les paramètres bt, bk et bm.
