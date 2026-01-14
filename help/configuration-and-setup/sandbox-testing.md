---
description: 'Test de l’intégration de Marketo Measure avec un sandbox Salesforce : conseils pour les utilisateurs de Marketo Measure'
title: Test de l’intégration de Marketo Measure à un sandbox Salesforce
exl-id: df40b000-4572-46df-aef5-8f690ca8ed7a
feature: Salesforce
source-git-commit: fcd8e276c85669ddf12bd7404fb12d3e99b2642a
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 10%

---

# Test de l’intégration de Marketo Measure à un sandbox Salesforce {#testing-the-marketo-measure-integration-with-a-salesforce-sandbox}

>[!NOTE]
>
>Des instructions spécifiant « [!DNL Marketo Measure] » peuvent s’afficher dans la documentation. Toutefois, votre gestion de la relation client (CRM) mentionne encore « Bizible ». Nous nous efforçons de mettre cela à jour. Notre nouvelle identité de marque (rebranding) sera bientôt répercutée dans votre CRM.

L’une des [!DNL Marketo Measure] fonctionnalités principales est sa capacité à suivre vos efforts de marketing numérique par le biais d’actions sur votre site web, puis à transmettre ces données à votre [!DNL Salesforce org] de production par le biais de prospects et de contacts. Cependant, en règle générale, aucun prospect entrant n’est créé à partir de votre site web dans une intégration Sandbox. Par conséquent, l’accent est mis sur les données d’un point de vue purement hors ligne.

Voici les deux sources référencées pour les deux phases du test. [étapes 1 à 4](https://help.salesforce.com/s/articleView?id=lead_import_wizard.htm&language=en_US&type=5) et [étapes 5 à 6](/help/channel-tracking-and-setup/syncing-offline-campaigns.md). Il est recommandé d’examiner ces documents car ils fournissent plus de détails dans certains domaines.

1. Vous devez créer des prospects dans un fichier CSV afin de pouvoir les charger dans une campagne. Pour ce faire, vous pouvez exporter des prospects par le biais d’un rapport dans votre Salesforce de production. Sinon, vous pouvez créer manuellement des prospects dans un fichier Excel, puis les enregistrer au format CSV en vue de les importer. Il suffit d&#39;une vingtaine d&#39;enregistrements. Le fichier doit avoir les colonnes suivantes :

   1. E-mail
   1. Société
   1. Nom
   1. Prénom (facultatif mais recommandé)

1. Connectez-vous à votre environnement Sandbox.
1. Créez une campagne de test. Utilisez un type de campagne comme Événement ou Newsletter.
1. Une fois la campagne créée, chargez les leads en tant que membres de campagne en sélectionnant **[!UICONTROL Gérer les membres]** > **[!UICONTROL Ajouter des membres]** > **[!UICONTROL Importer des fichiers]**.
1. Une fois cette opération terminée, revenez à la mise en page de la campagne et sélectionnez « Activer les points de contact de l’acheteur », qui est un champ de liste de sélection. Choisissez la valeur : **[!UICONTROL Inclure tous les membres de la campagne]**.

Une fois cette opération terminée, une synchronisation entre [!DNL Marketo Measure] et [!DNL Salesforce] est lancée et des points de contact sont appliqués aux enregistrements de leads. Il est recommandé de vérifier de nouveau le lendemain dans un rapport intitulé « Buyer Touchpoint on Leads » qui se trouve dans le dossier [!UICONTROL Rapports des points de contact de l’acheteur] sous l’onglet Rapports. Si le rapport renseigne un point de contact pour chaque prospect, c’est un signe de succès.
