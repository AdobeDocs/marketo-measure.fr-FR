---
description: Conseils sur la réautorisation des comptes connectés pour les utilisateurs de Marketo Measure
title: Réautorisation de comptes connectés
exl-id: 7abd1d67-5bed-45bb-844f-0ffd23c3d7f8
feature: APIs, Integration
hidefromtoc: true
source-git-commit: 7a4661c8d42214d32e5360dc45d6d880b08ef37c
workflow-type: tm+mt
source-wordcount: '208'
ht-degree: 4%

---

# Réautorisation de comptes connectés {#reauthorizing-connected-accounts}

Lorsqu’un compte est déconnecté de votre compte [!DNL Marketo Measure], le statut de la plateforme passe à « Autorisation requise » et une icône clé rouge s’affiche.

Si votre plateforme publicitaire est déconnectée, [!DNL Marketo Measure] ne pourrez pas télécharger les données de coût ou, si le balisage automatique est activé, ajouter les paramètres UTM [!DNL Marketo Measure] à toute nouvelle publicité. [!DNL Marketo Measure] ne pourra pas ajouter rétroactivement les paramètres UTM aux points de contact créés à partir de la plateforme publicitaire pendant la déconnexion du compte.

Si votre plateforme CRM est déconnectée, [!DNL Marketo Measure] ne pourrez pas mettre à jour [!DNL Marketo Measure] données ni transmettre de nouveaux points de contact à votre organisation. Une fois la connexion CRM rétablie, [!DNL Marketo Measure] transmet toutes les données qui ont été manquantes lors de la déconnexion du compte.

![Si votre plateforme CRM est déconnectée, Marketo Measure ne le sera pas](assets/utilizing-connections-7.png)

## Réautorisation des comptes déconnectés {#re-authorizing-disconnected-accounts}

1. Accédez à [experience.adobe.com/marketo-measure](https://experience.adobe.com/marketo-measure){target="_blank"} et connectez-vous.
1. Sélectionnez **[!UICONTROL Paramètres]** sous l’onglet [!UICONTROL  Mon compte] dans le coin supérieur gauche.
1. Recherchez la section Intégrations sur la gauche et cliquez sur **[!UICONTROL Connexions]**.
1. Sélectionnez le symbole de la clé rouge en regard du compte qui doit être reconnecté.
1. Une fenêtre pop-up s’affiche, vous invitant à fournir les informations de connexion au compte.
