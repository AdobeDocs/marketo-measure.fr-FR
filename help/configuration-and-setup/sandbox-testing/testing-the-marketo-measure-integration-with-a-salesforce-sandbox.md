---
unique-page-id: 18874765
description: Test de l’intégration Marketo Measure avec un environnement de test Salesforce - [!DNL Marketo Measure] - Documentation du produit
title: Test de l’intégration Marketo Measure avec un environnement de test Salesforce
exl-id: df40b000-4572-46df-aef5-8f690ca8ed7a
source-git-commit: 993a326c377b3b6ff48c4e0114b59297f9ca2ca6
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 1%

---

# Test de l’intégration Marketo Measure avec un environnement de test Salesforce {#testing-the-marketo-measure-integration-with-a-salesforce-sandbox}

>[!NOTE]
>
>Vous pouvez voir des instructions spécifiant &quot;[!DNL Marketo Measure]&quot; dans notre documentation, mais consultez toujours &quot;Bizible&quot; dans votre CRM. Nous nous efforçons de mettre à jour cette version et la nouvelle image sera bientôt répercutée dans votre CRM.

L’un des [!DNL Marketo Measure] les fonctionnalités principales sont sa capacité à suivre vos efforts de marketing numérique par le biais d’actions sur votre site web, puis à transmettre ces données à votre production. [!DNL Salesforce org] par le biais de pistes et de contacts. Cependant, il n’existe généralement pas de pistes entrantes créées à partir de votre site web dans une intégration Sandbox. Par conséquent, l’accent mis sur les données sera uniquement mis hors ligne.

Voici les deux sources référencées pour les deux phases du test. [Étapes 1 à 4](https://help.salesforce.com/apex/HTViewHelpDoc?id=lead_import_wizard.htm&amp;language=en_US) et [Étapes 5 à 6](/help/channel-tracking-and-setup/offline-channels/syncing-offline-campaigns.md). Nous vous recommandons de consulter ces documents, car ils fournissent davantage de détails dans certains domaines.

1. Vous devez créer des pistes dans un fichier CSV afin de pouvoir les télécharger dans une campagne. Pour ce faire, exportez des pistes par le biais d’un rapport dans votre Salesforce de production. Dans le cas contraire, vous pouvez créer manuellement des pistes dans un fichier Excel, puis les enregistrer au format CSV en vue de l’importer. Vous n&#39;avez besoin que d&#39;environ 20 enregistrements. Le fichier doit contenir les colonnes suivantes :

   1. Adresse e-mail
   1. Société
   1. Nom
   1. Prénom (facultatif mais recommandé)

1. Connectez-vous à votre environnement Sandbox.
1. Vous allez d’abord créer une campagne de test. Nous vous recommandons d’utiliser un type de campagne tel que Événement ou Newsletter.
1. Une fois la campagne créée, vous téléchargerez les pistes en tant que membres de campagne en sélectionnant **[!UICONTROL Gestion des membres]** > **[!UICONTROL Ajouter des membres]** > **[!UICONTROL Importer des fichiers]**.
1. Une fois cette opération terminée, de nouveau dans la mise en page de Campaign, vous allez &quot;Activer les points de contact d’achat&quot;, qui est un champ de liste de sélection. Sélectionnez la valeur : **[!UICONTROL Inclure tous les membres de campagne]**.

Une fois cette opération effectuée, une synchronisation entre [!DNL Marketo Measure] et [!DNL Salesforce] et appliquer des points de contact aux enregistrements de piste. Il est recommandé de vérifier le lendemain par le biais d’un rapport intitulé : &quot;Point de contact de l’achat sur les pistes&quot; figurant dans [!UICONTROL Rapports Points de contact d’achat] dans l’onglet Rapports . Si le rapport renseigne un point de contact pour chaque piste, c’est un signe de succès.
