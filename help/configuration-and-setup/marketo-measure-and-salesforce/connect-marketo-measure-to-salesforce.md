---
unique-page-id: 18874580
description: Connexion de la mesure Marketo à Salesforce - [!DNL Marketo Measure] - Documentation du produit
title: Connexion de la mesure Marketo à Salesforce
exl-id: 9be8d3fa-1045-4e41-bc2e-5b9d4d3513ae
source-git-commit: 993a326c377b3b6ff48c4e0114b59297f9ca2ca6
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 0%

---

# Connexion de la mesure Marketo à Salesforce {#connect-marketo-measure-to-salesforce}

Cet article présente un aperçu de la façon de connecter votre [!DNL Salesforce] de votre compte [!DNL Marketo Measure] compte .

## Connexion [!DNL Marketo Measure] avec [!DNL Salesforce] {#connecting-marketo-measure-with-salesforce}

1. Utilisez un navigateur incognito pour vous connecter à [!DNL Marketo Measure].

1. Dans la barre de menus en haut de l’écran, accédez à **[!UICONTROL Mon compte]** et cliquez sur le bouton [!UICONTROL Paramètres] .

1. Dans la colonne des options de paramétrage située à gauche, cliquez sur [!UICONTROL Connexions] situé sous le [!UICONTROL Intégrations] .

   ![](assets/1.png)

1. Sous la section CRM dans Connexions, cliquez sur **[!UICONTROL Configurer une nouvelle connexion CRM]**.

   ![](assets/2.png)

1. Une fenêtre contextuelle s&#39;affiche vous demandant de sélectionner la connexion CRM. Cliquez sur le bouton [!UICONTROL Connexion] en regard du bouton [!DNL Salesforce] logo.

   ![](assets/3.png)

1. Une dernière fenêtre contextuelle s’affiche, vous demandant de [!DNL Salesforce] informations d’identification, environnement de test ou production. Saisissez vos informations et cliquez sur **[!UICONTROL Autoriser]** pour connecter le compte à [!DNL Marketo Measure].

>[!NOTE]
>
>[!DNL Marketo Measure] ne peut être connecté qu’à un seul [!DNL Salesforce] instance à la fois.
>
>* A [!DNL Marketo Measure] L’instance peut être connectée à une instance Sandbox SFDC pour tester l’intégration avant de basculer vers votre instance de production SFDC.
>* Si vous testez d’abord avec un environnement de test SFDC, nous vous recommandons vivement d’en tester un qui est une réplique exacte de votre instance de production SFDC en termes de champs sur les objets Lead, Contact, Account, Opportunity, Campaign et Case. Si vous disposez de déclencheurs APEX principaux en production qui se déclenchent lors des mises à jour des objets Lead, Contact, Account, Opportunity, Campaign et Case, vous devez essayer de les placer principal dans votre environnement de test.
>* Une fois le test terminé, vous allez mettre à jour votre [!DNL Marketo Measure] compte à pointer vers votre environnement de production [!DNL Salesforce] (au lieu de sandbox) [!DNL Salesforce]). En raison de la manière dont l’intégration a été créée, une fois par [!DNL Marketo Measure] compte connecté à Production [!DNL Salesforce], vous ne pouvez pas revenir en arrière et vous connecter à un environnement de test. [!DNL Salesforce] org.


