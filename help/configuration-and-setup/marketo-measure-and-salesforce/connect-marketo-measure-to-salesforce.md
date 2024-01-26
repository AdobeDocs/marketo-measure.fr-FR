---
unique-page-id: 18874580
description: Connexion de Marketo Measure à Salesforce - [!DNL Marketo Measure] - Documentation du produit
title: Connexion de Marketo Measure à Salesforce
exl-id: 9be8d3fa-1045-4e41-bc2e-5b9d4d3513ae
feature: Salesforce
source-git-commit: b7aea1e0789b2f4f3fd4b250c0f66595618317bb
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 0%

---

# Connexion de Marketo Measure à Salesforce {#connect-marketo-measure-to-salesforce}

Cet article présente un aperçu de la façon de connecter votre [!DNL Salesforce] de votre compte [!DNL Marketo Measure] compte .

## Connexion [!DNL Marketo Measure] avec [!DNL Salesforce] {#connecting-marketo-measure-with-salesforce}

1. Utilisez un navigateur incognito pour vous connecter à [!DNL Marketo Measure].

1. Dans la barre de menus en haut de l’écran, accédez à **[!UICONTROL Mon compte]** et cliquez sur le bouton **[!UICONTROL Paramètres]** .

1. Dans la colonne des options de paramétrage située à gauche, cliquez sur **[!UICONTROL Connexions]** situé sous le [!UICONTROL Intégrations] .

   ![](assets/connect-marketo-measure-to-salesforce-1.png)

1. Sous la section CRM dans Connexions, cliquez sur **[!UICONTROL Configurer une nouvelle connexion CRM]**.

   ![](assets/connect-marketo-measure-to-salesforce-2.png)

1. Une fenêtre contextuelle s&#39;affiche vous demandant de sélectionner la connexion CRM. Cliquez sur le bouton **[!UICONTROL Connexion]** en regard du bouton [!DNL Salesforce] logo.

   ![](assets/connect-marketo-measure-to-salesforce-3.png)

1. Une dernière fenêtre contextuelle s’affiche, vous demandant de [!DNL Salesforce] informations d’identification, environnement de test ou production. Saisissez vos informations et cliquez sur **[!UICONTROL Autoriser]** pour connecter le compte à [!DNL Marketo Measure].

>[!NOTE]
>
>[!DNL Marketo Measure] ne peut être connecté qu’à un seul [!DNL Salesforce] instance à la fois.
>
>* A [!DNL Marketo Measure] L’instance peut être connectée à une instance Sandbox SFDC pour tester l’intégration avant de basculer vers votre instance de production SFDC.
>* Si vous testez d’abord avec un environnement de test SFDC, nous vous recommandons vivement d’en tester un qui est une réplique exacte de votre instance de production SFDC en termes de champs sur les objets Lead, Contact, Account, Opportunity, Campaign et Case. Si des triggers APEX actifs en production se déclenchent lors des mises à jour des objets Lead, Contact, Account, Opportunity, Campaign et Case, essayez de les activer dans votre environnement de test.
>* Une fois le test terminé, vous allez mettre à jour votre [!DNL Marketo Measure] compte à pointer vers votre environnement de production [!DNL Salesforce] (au lieu de sandbox) [!DNL Salesforce]). En raison de la manière dont l’intégration a été créée, une fois par [!DNL Marketo Measure] compte connecté à Production [!DNL Salesforce], vous ne pouvez pas revenir en arrière et vous connecter à un environnement de test. [!DNL Salesforce] org.

## Utilisation des crédits API {#api-credits-usage}

Marketo Measure utilise une tâche d’intégration CRM pour interagir avec Salesforce d’un client par le biais d’un utilisateur intégré. Tous les échanges de données via cet utilisateur utilisent des crédits API Salesforce. Vous avez la possibilité d’allouer un quota de crédit à un utilisateur d’intégration, qui sert à réguler les appels API excessifs. Ce quota ou cette limite est réinitialisé toutes les 24 heures.

Vous pouvez accéder à cette limite dans Marketo Measure via : **Mon compte** > **Paramètres** > **CRM** > **Général** > **Limite de l&#39;API CRM quotidienne** et peut le configurer pour vos clients.

![](assets/connect-marketo-measure-to-salesforce-4.png)

### Définition d’une limite pour les créations d’API {#setting-a-limit-for-api-credits}

1. Accédez à **Mon compte** > **Paramètres**.

1. Sous CRM, cliquez sur **Général**. Vous verrez le **Limite de l&#39;API CRM quotidienne** .

1. Cliquez sur l’icône représentant un cadenas pour la modifier.

   ![](assets/connect-marketo-measure-to-salesforce-5.png)

1. Saisissez une limite supérieure ou égale à 100 000. Cliquez sur **Enregistrer** une fois terminé.

   ![](assets/connect-marketo-measure-to-salesforce-6.png)

>[!NOTE]
>
>Pour augmenter les crédits d’API Salesforce disponibles pour votre solution connectée, contactez votre administrateur Salesforce et reportez-vous aux [ce document Salesforce ;](https://developer.salesforce.com/docs/atlas.en-us.salesforce_app_limits_cheatsheet.meta/salesforce_app_limits_cheatsheet/salesforce_app_limits_platform_api.htm){target="_blank"}.

>[!MORELIKETHIS]
>
>[Notifications d’erreur](/help/configuration-and-setup/getting-started-with-marketo-measure/error-notifications.md){target="_blank"}
