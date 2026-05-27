---
unique-page-id: 18874690
description: Autorisation de nouveau des comptes connectés - [!DNL Marketo Measure]
title: Réautorisation de comptes connectés
exl-id: 7abd1d67-5bed-45bb-844f-0ffd23c3d7f8
feature: APIs, Integration
TQID: https://experienceleague.adobe.com/mp53G9-w1l43mBQM1ijW8tTh7rNQ75cPAimZA-kdLvs
product_v2:
  - id: e6fc4016-a972-4f36-8c30-a6a5f82ad0c8
feature_v2:
  - id: c8f57308-7e33-4e41-a385-b55041c78939
  - id: fb43f4c1-87d9-4081-8df1-6fe7e6e5cdc8
source-git-commit: 9ceb54139bfa9b6ce7c2c5fbb4e25e649f5708a3
workflow-type: tm+mt
source-wordcount: 192
ht-degree: 5%

---

# Réautorisation de comptes connectés {#reauthorizing-connected-accounts}

Lorsqu’un compte est déconnecté de votre compte [!DNL Marketo Measure], le statut de la plateforme passe à « Autorisation requise » et une icône clé rouge s’affiche.

Si votre plateforme publicitaire est déconnectée, [!DNL Marketo Measure] ne pourrez pas télécharger les données de coût ou, si le balisage automatique est activé, ajouter les paramètres UTM [!DNL Marketo Measure] à toute nouvelle publicité. [!DNL Marketo Measure] ne pourra pas ajouter rétroactivement les paramètres UTM aux points de contact créés à partir de la plateforme publicitaire tant que le compte aura été déconnecté.

Si votre plateforme CRM est déconnectée, [!DNL Marketo Measure] ne pourrez pas mettre à jour [!DNL Marketo Measure] données ni transmettre de nouveaux points de contact à votre organisation. Une fois la connexion CRM rétablie, [!DNL Marketo Measure] transmet toutes les données qui ont été manquantes lors de la déconnexion du compte.

![](assets/1-1.png)

## Réautorisation des comptes déconnectés {#re-authorizing-disconnected-accounts}

1. Accédez à [&#128279;](https://experience.adobe.com/marketo-measure){target="_blank"} et connectez-vous.
1. Sélectionnez **[!UICONTROL Paramètres]** sous l’onglet [!UICONTROL &#x200B; Mon compte] dans le coin supérieur gauche.
1. Recherchez la section Intégrations sur la gauche et cliquez sur **[!UICONTROL Connexions]**.
1. Sélectionnez le symbole de la clé rouge en regard du compte qui doit être reconnecté.
1. Une fenêtre pop-up s’affiche, vous invitant à fournir les informations de connexion au compte.
