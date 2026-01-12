---
description: Migration de l’instance sandbox de Salesforce vers la production -  [!DNL Marketo Measure]
title: Migration de l’instance sandbox de Salesforce vers la production
exl-id: b2b71c4a-f192-43ce-a27e-cbd0ec3cf008
feature: Salesforce
source-git-commit: c6090ce0c3ac60cd68b1057c369ce0b3b20aeeee
workflow-type: tm+mt
source-wordcount: '322'
ht-degree: 95%

---


# Migration de l’instance sandbox de Salesforce vers la production {#salesforce-sandbox-to-production-migration}

Si vous choisissez de tester [!DNL Marketo Measure] dans un environnement sandbox de [!DNL Salesforce], suivez ces instructions pour migrer en production une fois que vous êtes en mesure de le faire. Les instructions suivantes supposent que vous avez déjà téléchargé le package [!DNL Marketo Measure] dans votre organisation sandbox, effectué les tests nécessaires et que vous êtes en mesure d’effectuer des envois [!DNL Marketo Measure] en production.

## Étape 1 : installer le package [!DNL Marketo Measure] dans votre instance [!DNL Salesforce] de production

* Installer le package [!DNL Marketo Measure] en production avec le paramètre « [!UICONTROL Tous les utilisateurs et utilisatrices] »

   * [Package de base](https://appexchange.salesforce.com/appxListingDetail?listingId=a0N3000000B3KLuEAN){target="_blank"}

* Pour plus d’informations sur la relation entre [!DNL Marketo Measure] et [!DNL Salesforce], consultez [cet article](/help/configuration-and-setup/marketo-measure-and-salesforce/how-marketo-measure-and-salesforce-interact.md).
* Une légère configuration de [!DNL Salesforce] est nécessaire. Les actions spécifiques sont décrites dans l’[Étape 4 ci-dessous](#salesforce-configuration).

## Étape 2 : supprimer la connexion CRM de sandbox actuelle dans l’application [!DNL Marketo Measure] {#delete-the-current-sandbox-crm-connection-in-marketo-measure-app}

* Connectez-vous à l’application [!DNL Marketo Measure] à l’adresse experience.adobe.com/marketo-measure.
* Accédez à Mon compte > [!UICONTROL Paramètres] > [!UICONTROL Connexions].
* Cliquez sur l’icône de la corbeille en regard de la connexion SFDC à supprimer.
* Vous recevez une invitation à confirmer la suppression. Veillez à lire attentivement le prompt et à comprendre les conséquences de la suppression.

  ![page de connexions Marketo Measure confirmant la suppression d’un sandbox Salesforce](assets/salesforce-sandbox-to-production-migration-1.png)

   * Saisissez le nom de l’entreprise, comme indiqué dans le modèle de confirmation, puis cliquez sur « Je comprends les conséquences, supprimer cette connexion ».
* Le processus de suppression est déclenché et son exécution prend un certain temps.

## Étape 3 : se connecter à l’instance CRM en production dans l’application [!DNL Marketo Measure] {#connect-the-production-crm-instance-in-marketo-measure-app}

* Connectez-vous à l’application [!DNL Marketo Measure] à l’adresse experience.adobe.com/marketo-measure.
* Accédez à [!UICONTROL Mon compte] > [!UICONTROL Paramètres] > [!UICONTROL Connexions].
* Une fois la connexion de sandbox correctement supprimée, la connexion disparaît de la page. Sinon, la connexion reste présente avec le statut « Suppression en cours ».
* Cliquez sur « [!UICONTROL Configurer une nouvelle connexion CRM] ».
* Dans la boîte de dialogue modale « [!UICONTROL Sélectionner la connexion CRM] », cliquez sur l’action « [!UICONTROL Se connecter] » en regard de la plateforme [!DNL Salesforce], puis sélectionnez l’option « [!UICONTROL Production] ».
* Vous recevez une invitation à saisir vos informations d’identification. Veillez à saisir les informations de connexion de production.

## Étape 4 : configurer Salesforce {#salesforce-configuration}

[Dispositions de page](/help/configuration-and-setup/marketo-measure-and-salesforce/page-layout-instructions.md)

[Jeux d’autorisations](/help/configuration-and-setup/marketo-measure-and-salesforce/marketo-measure-permission-sets.md)

[Partage de rapports &#x200B;](https://help.salesforce.com/s/articleView?language=en_US&id=analytics_share_folder.htm&type=0){target="_blank"}

[Masquer les types de rapports superflus](/help/configuration-and-setup/marketo-measure-and-salesforce/hiding-unnecessary-report-types.md)

[Workflow personnalisé, le cas échéant](/help/advanced-features/custom-revenue-amount/using-a-custom-revenue-amount-field.md)
