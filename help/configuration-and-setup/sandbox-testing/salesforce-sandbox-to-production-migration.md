---
unique-page-id: 18874694
description: Migration de l’environnement de test Salesforce vers la production - [!DNL Marketo Measure] - Documentation du produit
title: Migration de l’environnement de test Salesforce vers la production
exl-id: b2b71c4a-f192-43ce-a27e-cbd0ec3cf008
source-git-commit: b59c79236d3e324e8c8b07c5a6d68bd8176fc8a9
workflow-type: tm+mt
source-wordcount: '347'
ht-degree: 0%

---

# Migration de l’environnement de test Salesforce vers la production {#salesforce-sandbox-to-production-migration}

Si vous choisissez de tester [!DNL Marketo Measure] dans [!DNL Salesforce] Environnement Sandbox, suivez ces instructions pour migrer vers Production une fois que vous êtes prêt. Les instructions suivantes supposent que vous avez déjà téléchargé la variable [!DNL Marketo Measure] module dans votre organisation Sandbox, effectuez les tests nécessaires et êtes prêt à effectuer des notifications push. [!DNL Marketo Measure] vers Production.

## Étape 1 : Installer [!DNL Marketo Measure] Modules dans votre production [!DNL Salesforce] Instance {#install-marketo-measure-packages-into-your-production-salesforce-instance}

* Installez les deux [!DNL Marketo Measure] modules en production avec le[!UICONTROL Tous les utilisateurs]paramètre &quot;

   * [Package de base](https://appexchange.salesforce.com/appxListingDetail?listingId=a0N3000000B3KLuEAN){target=&quot;_blank&quot;}
   * [Package d’extension de tableau de bord](https://login.salesforce.com/packaging/installPackage.apexp?p0=04t610000001jI6){target=&quot;_blank&quot;}

* Pour plus d’informations sur la variable [!DNL Marketo Measure] relation avec [!DNL Salesforce], reportez-vous à la section [cet article](/help/configuration-and-setup/marketo-measure-and-salesforce/how-marketo-measure-and-salesforce-interact.md)
* Un peu de [!DNL Salesforce] est nécessaire. Les actions spécifiques sont décrites ci-dessous dans la section [Étape 4 ci-dessous](#salesforce-configuration)

## Étape 2 : Suppression de la connexion CRM Sandbox actuelle dans [!DNL Marketo Measure] Application {#delete-the-current-sandbox-crm-connection-in-marketo-measure-app}

* Connectez-vous au [!DNL Marketo Measure] application à l’adresse experience.adobe.com/marketo-measure
* Accédez à Mon compte >[!UICONTROL Paramètres] >[!UICONTROL Connexions]
* Cliquez sur l’icône de corbeille en regard de votre connexion SFDC pour la supprimer.
* Vous serez invité à confirmer votre suppression. Veillez à lire attentivement l’invite et à comprendre les conséquences de la suppression.

   ![](assets/salesforce-sandbox-to-production-migration-1.png)

   * Saisissez le nom de l’entreprise, comme indiqué dans le modèle de confirmation, puis cliquez sur &quot;Je comprends les conséquences, supprimez cette connexion&quot;.
* Cela déclenchera le processus de suppression et prendra du temps.

## Étape 3 : Connexion de l’instance CRM de production dans [!DNL Marketo Measure] Application {#connect-the-production-crm-instance-in-marketo-measure-app}

* Connectez-vous au [!DNL Marketo Measure] application à l’adresse experience.adobe.com/marketo-measure
* Accédez à [!UICONTROL Mon compte] >[!UICONTROL Paramètres] > [!UICONTROL Connexions]
* Une fois la suppression de la connexion Sandbox supprimée, la connexion disparaît de la page, sinon la connexion reste présente avec le statut &quot;Suppression en cours&quot;.
* Cliquez sur &quot;[!UICONTROL Configurer une nouvelle connexion CRM]&quot;
* Dans le[!UICONTROL Sélectionner la connexion CRM]&quot;, dans la boîte de dialogue modale, cliquez sur &quot;[!UICONTROL Connexion]&quot; Action en regard de la variable [!DNL Salesforce] Platform, sélectionnez le[!UICONTROL Production]Option &quot;
* Vous serez invité à saisir vos informations d’identification. Veillez à saisir les informations de connexion à la production.

## Étape 4 : Configuration Salesforce {#salesforce-configuration}

[Mises en page](/help/configuration-and-setup/marketo-measure-and-salesforce/page-layout-instructions.md)

[Jeux d’autorisations](/help/configuration-and-setup/marketo-measure-and-salesforce/marketo-measure-permission-sets.md)

[Partage de rapports](https://help.salesforce.com/articleView?id=analytics_share_folder.htm&amp;type=0){target=&quot;_blank&quot;}

[Masquage des types de rapports inutiles](/help/configuration-and-setup/marketo-measure-and-salesforce/hiding-unnecessary-report-types.md)

[Processus personnalisé, le cas échéant](/help/advanced-marketo-measure-features/custom-revenue-amount/using-a-custom-revenue-amount-field.md)
