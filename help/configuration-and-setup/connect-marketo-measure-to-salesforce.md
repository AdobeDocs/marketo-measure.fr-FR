---
description: Conseils pour la connexion de Marketo Measure à Salesforce pour les utilisateurs de Marketo Measure
title: Connexion de Marketo Measure à Salesforce
exl-id: 9be8d3fa-1045-4e41-bc2e-5b9d4d3513ae
feature: Salesforce
source-git-commit: fcd8e276c85669ddf12bd7404fb12d3e99b2642a
workflow-type: tm+mt
source-wordcount: '493'
ht-degree: 2%

---

# Connexion de Marketo Measure à Salesforce {#connect-marketo-measure-to-salesforce}

Cet article présente un aperçu de la connexion de votre compte [!DNL Salesforce] à votre compte [!DNL Marketo Measure].

## Connexion de [!DNL Marketo Measure] à [!DNL Salesforce] {#connecting-marketo-measure-with-salesforce}

1. Utilisez un navigateur incognito pour vous connecter à [!DNL Marketo Measure].

1. Dans la barre de menus en haut de l’écran, accédez à **[!UICONTROL Mon compte]** puis cliquez sur l’option **[!UICONTROL Paramètres]**.

1. Dans la colonne des options de configuration sur la gauche, cliquez sur **[!UICONTROL Connexions]** dans la section [!UICONTROL Intégrations].

   ![1. Dans la colonne des options de paramétrage sur la gauche, cliquez sur ](assets/bizible-full-1.png)

1. Sous la section CRM dans Connexions, cliquez sur **[!UICONTROL Configurer une nouvelle connexion CRM]**.

   ![1. Sous la section CRM dans Connexions, cliquez sur Configurer nouveau](assets/bizible-taxonomy-1.png)

1. Une fenêtre pop-up s’affiche vous demandant de Sélectionner la connexion CRM . Cliquez sur **[!UICONTROL Connexion]** en regard du logo [!DNL Salesforce].

   ![1. Une fenêtre pop-up s’affiche vous demandant de Sélectionner la connexion CRM . Cliquez sur ](assets/connect-salesforce-1.png)

1. Une dernière fenêtre pop-up s’affiche, vous demandant vos informations d’identification [!DNL Salesforce], votre sandbox ou votre environnement de production. Saisissez vos informations et cliquez sur **[!UICONTROL Autoriser]** pour connecter le compte à [!DNL Marketo Measure].

>[!NOTE]
>
>[!DNL Marketo Measure] ne peut être connecté qu’à une seule instance [!DNL Salesforce] à la fois.
>
>* Une instance [!DNL Marketo Measure] peut être connectée à une instance Sandbox SFDC pour tester l’intégration avant de passer à votre instance de production SFDC.
>* Si vous testez d’abord avec un sandbox SFDC, nous vous recommandons vivement d’en tester un qui est une réplique exacte de votre instance de production SFDC en termes de champs sur les objets Lead, Contact, Compte, Opportunité, Campagne et Cas . Si la production de déclencheurs APEX actifs se déclenche lors des mises à jour des objets Lead, Contact, Compte, Opportunité, Campagne et Dossier, vous devez essayer de les activer dans votre sandbox.
>* Une fois les tests terminés, vous mettez à jour votre compte [!DNL Marketo Measure] pour qu’il pointe vers votre [!DNL Salesforce] de production (au lieu de votre [!DNL Salesforce] Sandbox). En raison de la manière dont l’intégration a été créée, une fois qu’un compte [!DNL Marketo Measure] est connecté à l’[!DNL Salesforce] de production, vous ne pouvez pas revenir en arrière et vous connecter à une organisation [!DNL Salesforce] Sandbox.

## Utilisation des crédits API {#api-credits-usage}

Marketo Measure utilise une tâche d’intégration CRM pour s’interfacer avec le Salesforce d’un client par le biais d’un utilisateur intégré. Tous les échanges de données via cet utilisateur utilisent des crédits API Salesforce. Vous avez la possibilité d’allouer un quota de crédit à un utilisateur de l’intégration, ce qui permet de réguler les appels d’API excessifs. Ce quota ou cette limite est réinitialisé toutes les 24 heures.

Vous pouvez accéder à cette limite dans Marketo Measure via : **Mon compte** > **Paramètres** > **CRM** > **Général** > **Limite quotidienne de l’API CRM** et la configurer pour vos clients.

![Vous pouvez accéder à cette limite dans Marketo Measure via : Paramètres de mon compte](assets/connect-salesforce-2.png)

### Définition d’une limite pour les crédits API {#setting-a-limit-for-api-credits}

1. Accédez à **Mon compte** > **Paramètres**.

1. Sous CRM, cliquez sur **Général**. L’option **Limite quotidienne d’API CRM** s’affiche.

1. Cliquez sur l’icône Verrouiller pour modifier.

   ![1. Cliquez sur l’icône Verrouiller pour modifier.](assets/connect-salesforce-3.png)

1. Saisissez une limite souhaitée égale ou supérieure à 100 000. Cliquez sur **Enregistrer** lorsque vous avez terminé.

   ![1. Saisissez une limite souhaitée égale ou supérieure à 100 000. Cliquez sur ](assets/connect-salesforce-1.png)

>[!NOTE]
>
>Pour augmenter les crédits d’API Salesforce disponibles pour votre solution connectée, contactez votre administrateur Salesforce et référencez [ce document Salesforce](https://developer.salesforce.com/docs/atlas.en-us.salesforce_app_limits_cheatsheet.meta/salesforce_app_limits_cheatsheet/salesforce_app_limits_platform_api.htm){target="_blank"}.

>[!MORELIKETHIS]
>
>[Notifications d’erreur](/help/configuration-and-setup/error-notifications.md){target="_blank"}
