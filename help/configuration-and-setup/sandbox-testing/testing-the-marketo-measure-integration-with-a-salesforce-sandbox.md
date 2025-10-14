---
unique-page-id: 18874765
description: Test de l’intégration Marketo Measure avec un sandbox Salesforce - [!DNL Marketo Measure]
title: Test de l’intégration Marketo Measure avec un environnement de test Salesforce
exl-id: df40b000-4572-46df-aef5-8f690ca8ed7a
feature: Salesforce
source-git-commit: 741ab20845de2f3bcde589291d7446a5b4f877d8
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 10%

---

# Test de l’intégration Marketo Measure avec un environnement de test Salesforce {#testing-the-marketo-measure-integration-with-a-salesforce-sandbox}

>[!NOTE]
>
>Des instructions spécifiant « [!DNL Marketo Measure] » peuvent s’afficher dans la documentation. Toutefois, votre gestion de la relation client (CRM) mentionne encore « Bizible ». Nous nous efforçons de mettre cela à jour. Notre nouvelle identité de marque (rebranding) sera bientôt répercutée dans votre CRM.

L’une des fonctionnalités principales de [!DNL Marketo Measure] est sa capacité à suivre vos efforts de marketing numérique par le biais d’actions sur votre site web, puis à transmettre ces données à votre production [!DNL Salesforce org] par le biais de pistes et de contacts. Cependant, il n’existe généralement pas de pistes entrantes créées à partir de votre site web dans une intégration Sandbox. Par conséquent, l’accent mis sur les données sera uniquement mis hors ligne.

Voici les deux sources référencées pour les deux phases du test. [Étapes 1-4](https://help.salesforce.com/s/articleView?id=lead_import_wizard.htm&language=en_US&type=5) et [Étapes 5-6](/help/channel-tracking-and-setup/offline-channels/legacy-processes/syncing-offline-campaigns.md). Il est recommandé d’examiner ces documents, car ils fournissent davantage de détails dans certains domaines.

1. Vous devez créer des pistes dans un fichier CSV afin de pouvoir les télécharger dans une campagne. Pour ce faire, exportez des pistes par le biais d’un rapport dans votre Salesforce de production. Dans le cas contraire, vous pouvez créer manuellement des pistes dans un fichier Excel, puis les enregistrer au format CSV pour importation. Vous n&#39;avez besoin que d&#39;environ 20 enregistrements. Le fichier doit contenir les colonnes suivantes :

   1. E-mail
   1. Société
   1. Nom
   1. Prénom (facultatif mais recommandé)

1. Connectez-vous à votre environnement Sandbox.
1. Créez une campagne de test. Utilisez un type de campagne tel que Événement ou Newsletter.
1. Une fois la campagne créée, téléchargez les pistes en tant que membres de campagne en sélectionnant **[!UICONTROL Gérer les membres]** > **[!UICONTROL Ajouter des membres]** > **[!UICONTROL Importer des fichiers]**.
1. Une fois cette opération terminée, de nouveau dans la mise en page de Campaign, vous allez &quot;Activer les points de contact d’achat&quot;, qui est un champ de liste de sélection. Sélectionnez la valeur : **[!UICONTROL Include All Campaign Members]**.

Une fois cette opération terminée, une synchronisation entre [!DNL Marketo Measure] et [!DNL Salesforce] est déclenchée et des points de contact sont appliqués aux enregistrements de piste. Il est recommandé de vérifier le lendemain par le biais d’un rapport intitulé &quot;Buyer Touchpoint on Leads&quot; situé dans le dossier [!UICONTROL Rapports des points de contact client] de l’onglet Rapports. Si le rapport renseigne un point de contact pour chaque piste, c’est un signe de succès.
