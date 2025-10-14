---
unique-page-id: 18874706
description: Restrictions de session de sécurité - Adresses IP à Liste autorisée - Marketo Measure - Documentation du produit
title: Restrictions de session de sécurité - Adresses IP à Liste autorisée
exl-id: aaf5190f-893c-4872-8d03-93f516e70a59
feature: Tracking
source-git-commit: 8ac315e7c4110d14811e77ef0586bd663ea1f8ab
workflow-type: tm+mt
source-wordcount: '84'
ht-degree: 8%

---

# Restrictions de session de sécurité : adresses IP à placer sur la liste autorisée {#security-session-restrictions-ip-addresses-to-allowlist}

Si des [&#x200B; paramètres de sécurité de session](https://help.salesforce.com/articleView?id=admin_sessions.htm&type=0){target="_blank"} sont en place pour empêcher des adresses IP spécifiques de pousser/extraire des données vers votre instance [!DNL Salesforce], nous aurons besoin des plages d’adresses IP suivantes placées sur la liste autorisée pour permettre à [!DNL Marketo Measure] de transmettre des données vers [!DNL Salesforce] :

* 52.162.84.192 - 52.162.84.207
* 23.100.229.112 - 23.100.229.127
* 20.186.163.0 - 20.186.163.15

Pour ajouter [!DNL Marketo Measure] adresses IP aux plages d’adresses IP approuvées dans Salesforce, cliquez sur **[!UICONTROL Configuration]** > **[!UICONTROL Configuration de l’administration]** > **[!UICONTROL Contrôles de sécurité]** > **[!UICONTROL Accès réseau]** > **[!UICONTROL Nouveau]**.

![](assets/1.png)
