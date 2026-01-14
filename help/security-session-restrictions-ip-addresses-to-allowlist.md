---
description: Répertorie les plages d’adresses IP Salesforce à placer sur la liste autorisée pour que Marketo Measure puisse se connecter lorsque les restrictions de session sont appliquées
title: Restrictions de session de sécurité - Adresses IP à Placer sur la liste autorisée
exl-id: aaf5190f-893c-4872-8d03-93f516e70a59
feature: Tracking
source-git-commit: fcd8e276c85669ddf12bd7404fb12d3e99b2642a
workflow-type: tm+mt
source-wordcount: '94'
ht-degree: 7%

---

# Restrictions de session de sécurité : adresses IP à placer sur la liste autorisée {#security-session-restrictions-ip-addresses-to-allowlist}

Si des [paramètres de sécurité de session](https://help.salesforce.com/articleView?id=admin_sessions.htm&type=0){target="_blank"} sont en place, ce qui empêche des adresses IP spécifiques d’envoyer/extraire des données vers votre instance de [!DNL Salesforce], il faudra que les plages d’adresses IP suivantes soient placées sur la liste autorisée pour [!DNL Marketo Measure] permettre d’envoyer des données vers [!DNL Salesforce] :

* 52.162.84.192 - 52.162.84.207
* 23.100.229.112 - 23.100.229.127
* 20.186.163.0 - 20.186.163.15

Pour ajouter des adresses IP [!DNL Marketo Measure] aux plages d’adresses IP de confiance dans Salesforce, cliquez sur **[!UICONTROL Configuration]** > **[!UICONTROL Configuration de l’administration]** > **[!UICONTROL Contrôles de sécurité]** > **[!UICONTROL Accès réseau]** > **[!UICONTROL Nouveau]**.

![Pour ajouter des adresses IP Marketo Measure aux plages d’adresses IP de confiance dans ](assets/compliance-resources-1.png)
