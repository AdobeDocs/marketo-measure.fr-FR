---
unique-page-id: 18874706
description: Restrictions de session de sécurité - Adresses IP à inclure dans la Place sur la liste autorisée - Marketo Measure - Documentation du produit
title: Restrictions de session de sécurité - Adresses IP à Placer sur la liste autorisée
exl-id: aaf5190f-893c-4872-8d03-93f516e70a59
feature: Tracking
TQID: https://experienceleague.adobe.com/Ka7ff5qarBVEm4JdSGCbaUM3Mrug0r3ZOPSKPrnc3Zo
product_v2:
  - id: e6fc4016-a972-4f36-8c30-a6a5f82ad0c8
topic_v2:
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 9ceb54139bfa9b6ce7c2c5fbb4e25e649f5708a3
workflow-type: tm+mt
source-wordcount: 84
ht-degree: 8%

---

# Restrictions de session de sécurité : adresses IP à placer sur la liste autorisée {#security-session-restrictions-ip-addresses-to-allowlist}

Si des [paramètres de sécurité de session](https://help.salesforce.com/articleView?id=admin_sessions.htm&type=0){target="_blank"} sont en place, ce qui empêche des adresses IP spécifiques d’envoyer/extraire des données vers votre instance de [!DNL Salesforce], il faudra que les plages d’adresses IP suivantes soient placées sur la liste autorisée pour [!DNL Marketo Measure] permettre d’envoyer des données vers [!DNL Salesforce] :

* 52.162.84.192 - 52.162.84.207
* 23.100.229.112 - 23.100.229.127
* 20.186.163.0 - 20.186.163.15

Pour ajouter des adresses IP [!DNL Marketo Measure] aux plages d’adresses IP de confiance dans Salesforce, cliquez sur **[!UICONTROL Configuration]** > **[!UICONTROL Configuration de l’administration]** > **[!UICONTROL Contrôles de sécurité]** > **[!UICONTROL Accès réseau]** > **[!UICONTROL Nouveau]**.

![](assets/1.png)
