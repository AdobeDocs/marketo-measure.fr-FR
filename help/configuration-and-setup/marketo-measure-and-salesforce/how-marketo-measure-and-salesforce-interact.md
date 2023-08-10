---
unique-page-id: 18874672
description: Comment [!DNL Marketo Measure] et [!DNL Salesforce] Interact - Marketo Measure - Documentation du produit
title: Explication des interactions entre [!DNL Marketo Measure] et [!DNL Salesforce]
exl-id: c2f9d7ce-c5b8-4664-8f92-cb54255190cd
feature: Salesforce
source-git-commit: 8ac315e7c4110d14811e77ef0586bd663ea1f8ab
workflow-type: tm+mt
source-wordcount: '1680'
ht-degree: 36%

---

# Explication des interactions entre[!DNL Marketo Measure]et[!DNL Salesforce] {#how-marketo-measure-and-salesforce-interact}

>[!NOTE]
>
>Vous pouvez voir des instructions spécifiant &quot;[!DNL Marketo Measure]&quot; dans notre documentation, mais consultez toujours &quot;Bizible&quot; dans votre CRM. Nous nous efforçons de mettre à jour cette version et la nouvelle image sera bientôt répercutée dans votre CRM.

Regardons de plus près la relation entre [!DNL Marketo Measure] et Salesforce.

## Salesforce et [!DNL Marketo Measure] {#salesforce-and-marketo-measure}

Une fois que la variable [!DNL Marketo Measure] le compte est créé et [!DNL Salesforce] est connecté, [!DNL Marketo Measure] commencera à transférer les données marketing dans l’instance CRM tant que la variable [!DNL Marketo Measure] le module géré est installé et le [!DNL Marketo Measure] L’utilisateur Salesforce dispose de droits de modification.

Si vous n’avez pas installé le [!DNL Marketo Measure] package Salesforce, [!DNL Marketo Measure] n’écrira aucune donnée sur votre instance Salesforce.

![](assets/1-3.png)

Par défaut, [!DNL Marketo Measure] exporte 200 enregistrements par crédit d’API chaque fois qu’une tâche envoie des données à votre service de gestion de la relation client. Pour la plupart des clients, cela permet d’obtenir un équilibre optimal entre les crédits d’API consommés par [!DNL Marketo Measure] et les exigences en matière de ressources du processeur sur le CRM. Toutefois, pour les clients avec des configurations CRM complexes, comme les workflows et les triggers, une taille de lot réduite peut s’avérer utile pour améliorer les performances CRM. À cette fin, [!DNL Marketo Measure] permet aux clients de configurer la taille du lot d’exportation CRM. Ce paramètre est disponible dans la [!UICONTROL Paramètres] > [!UICONTROL CRM] > [!UICONTROL Général] dans la [!DNL Marketo Measure] l’application web et les clients peuvent choisir entre des tailles de lot de 200 (par défaut), 100, 50 ou 25.

![](assets/how-bizible-and-salesforce-interact-2.png)

Lorsque vous modifiez ce paramètre, gardez à l’esprit que des tailles de lots plus petites consommeront plus de crédits d’API de votre CRM. Il est conseillé de réduire la taille du lot uniquement si vous rencontrez un délai d’expiration du processeur ou une charge élevée du processeur dans votre CRM.

## Objets standard Salesforce et accès {#salesforce-standard-objects-and-access}

Cette section répertorie les [!DNL Salesforce] Objets standard [!DNL Marketo Measure] interagit avec, ainsi que les champs personnalisés que nous ajoutons à ces objets une fois la connexion établie et la fonction [!DNL Marketo Measure] est installé. Prêt à l’emploi, [!DNL Marketo Measure] n’écrira PAS dans une norme [!DNL Salesforce] Champs d’objet.

**Prospect**

<table> 
 <tbody> 
  <tr> 
   <th><p>Champs</p></th> 
   <th><p>Standard/Personnalisé</p></th> 
   <th><p>Lecture</p></th> 
   <th><p>Write</p></th> 
  </tr> 
  <tr> 
   <td><p>ID</p></td> 
   <td><p>Standard</p></td> 
   <td><p> x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>E-mail</p></td> 
   <td><p>Standard</p></td> 
   <td><p> x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>Statut</p></td> 
   <td><p>Standard</p></td> 
   <td><p> x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>Date de création</p></td> 
   <td><p>Standard</p></td> 
   <td><p> x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>LastModifiedDate</p></td> 
   <td><p>Standard</p></td> 
   <td><p> x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>ConvertedDate</p></td> 
   <td><p>Standard</p></td> 
   <td><p> x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>ConvertedContactId</p></td> 
   <td><p>Standard</p></td> 
   <td><p> x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>ConvertedOpportunityId</p></td> 
   <td><p>Standard</p></td> 
   <td><p> x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>IsConverted</p></td> 
   <td><p>Standard</p></td> 
   <td><p> x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>Est supprimé</p></td> 
   <td><p>Standard</p></td> 
   <td><p> x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>Site Internet</p></td> 
   <td><p>Standard</p></td> 
   <td><p> x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>Société</p></td> 
   <td><p>Standard</p></td> 
   <td><p> x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Account__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Ad_Campaign_Name_FT__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Ad_Campaign_Name_LC__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Landing_Page_FT__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Landing_Page_LC__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Marketing_Channel_FT__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Marketing_Channel_LC__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Touchpoint_Date_FT__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Touchpoint_Date_LC__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Touchpoint_Source_FT__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Touchpoint_Source_LC__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x </p></td> 
  </tr> 
 </tbody> 
</table>

**Contact**

<table> 
 <tbody> 
  <tr> 
   <th><p>Champs</p></th> 
   <th><p>Standard/Personnalisé</p></th> 
   <th><p>Lecture</p></th> 
   <th><p>Write</p></th> 
  </tr> 
  <tr> 
   <td><p>Compte</p></td> 
   <td><p>Standard</p></td> 
   <td><span> x</span></td> 
   <td><br></td> 
  </tr> 
  <tr> 
   <td><p>ID</p></td> 
   <td><p>Standard</p></td> 
   <td><p> x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>E-mail</p></td> 
   <td><p>Standard</p></td> 
   <td><p> x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>Date créée</p></td> 
   <td><p>Standard</p></td> 
   <td><p> x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>Est supprimé</p></td> 
   <td><p>Standard</p></td> 
   <td><p> x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>LastModifiedDate</p></td> 
   <td><p>Standard</p></td> 
   <td><p> x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Ad_Campaign_Name_FT__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Ad_Campaign_Name_LC__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Landing_Page_FT__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Landing_Page_LC__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Marketing_Channel_FT__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Marketing_Channel_LC__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Touchpoint_Date_FT__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Touchpoint_Date_LC__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Touchpoint_Source_FT__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Touchpoint_Source_LC__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x </p></td> 
  </tr> 
 </tbody> 
</table>

**Dossier**

<table> 
 <tbody> 
  <tr> 
   <th><p>Champs</p></th> 
   <th><p>Standard/Personnalisé</p></th> 
   <th><p>Lecture</p></th> 
   <th><p>Write</p></th> 
  </tr> 
  <tr> 
   <td><p>ID</p></td> 
   <td><p>Standard</p></td> 
   <td><p> x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>Date de création</p></td> 
   <td><p>Standard</p></td> 
   <td><p> x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>LastModifiedDate</p></td> 
   <td><p>Standard</p></td> 
   <td><p> x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>SuppliedEmail</p></td> 
   <td><p>Standard</p></td> 
   <td><p> x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>Est supprimé</p></td> 
   <td><p>Standard</p></td> 
   <td><p> x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Ad_Campaign_Name_FT__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Ad_Campaign_Name_LC__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Landing_Page_FT__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Landing_Page_LC__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Marketing_Channel_FT__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Marketing_Channel_LC__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Touchpoint_Date_FT__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Touchpoint_Date_LC__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Touchpoint_Source_FT__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Touchpoint_Source_LC__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x </p></td> 
  </tr> 
 </tbody> 
</table>

**Compte**

<table> 
 <tbody> 
  <tr> 
   <th><p>Champs</p></th> 
   <th><p>Standard/Personnalisé</p></th> 
   <th><p>Lecture</p></th> 
   <th><p>Write</p></th> 
  </tr> 
  <tr> 
   <td><p>ID</p></td> 
   <td><p>Standard</p></td> 
   <td><p> x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>Site Internet</p></td> 
   <td><p>Standard</p></td> 
   <td><p> x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>LastModifiedDate</p></td> 
   <td><p>Standard</p></td> 
   <td><p> x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>Est supprimé</p></td> 
   <td><p>Standard</p></td> 
   <td><p> x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Engagement_Score__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x </p></td> 
  </tr> 
 </tbody> 
</table>

**Opportunité**

<table> 
 <tbody> 
  <tr> 
   <th><p>Champs</p></th> 
   <th><p>Standard/Personnalisé</p></th> 
   <th><p>Lecture</p></th> 
   <th><p>Write</p></th> 
  </tr> 
  <tr> 
   <td><p>Compte</p></td> 
   <td><p>Standard</p></td> 
   <td><p> x</p></td> 
   <td><br></td> 
  </tr> 
  <tr> 
   <td><p>ID</p></td> 
   <td><p>Standard</p></td> 
   <td><p> x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>Date de création</p></td> 
   <td><p>Standard</p></td> 
   <td><p> x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>LastModifiedDate</p></td> 
   <td><p>Standard</p></td> 
   <td><p> x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>IsWon</p></td> 
   <td><p>Standard</p></td> 
   <td><p> x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>IsClosed</p></td> 
   <td><p>Standard</p></td> 
   <td><p> x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>Est supprimé</p></td> 
   <td><p>Standard</p></td> 
   <td><p> x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>CloseDate</p></td> 
   <td><p>Standard</p></td> 
   <td><p> x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>StageName</p></td> 
   <td><p>Standard</p></td> 
   <td><p> x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>Montant</p></td> 
   <td><p>Standard</p></td> 
   <td><p> x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Bizible_Opportunity_Amount__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x </p></td> 
  </tr> 
 </tbody> 
</table>

**Campagne**

<table> 
 <colgroup> 
  <col> 
  <col> 
  <col> 
  <col> 
 </colgroup> 
 <tbody> 
  <tr> 
   <th><p>Champs</p></th> 
   <th><p>Standard/Personnalisé</p></th> 
   <th><p>Lecture</p></th> 
   <th><p>Write</p></th> 
  </tr> 
  <tr> 
   <td><p>ID</p></td> 
   <td><p>Standard</p></td> 
   <td><p> x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>E-mail</p></td> 
   <td><p>Standard</p></td> 
   <td><p> x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>Statut</p></td> 
   <td><p>Standard</p></td> 
   <td><p> x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>Date de création</p></td> 
   <td><p>Standard</p></td> 
   <td><p> x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>LastModifiedDate</p></td> 
   <td><p>Standard</p></td> 
   <td><p> x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>ConvertedDate</p></td> 
   <td><p>Standard</p></td> 
   <td><p> x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>ConvertedContactId</p></td> 
   <td><p>Standard</p></td> 
   <td><p> x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>ConvertedOpportunityId</p></td> 
   <td><p>Standard</p></td> 
   <td><p> x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>IsConverted</p></td> 
   <td><p>Standard</p></td> 
   <td><p> x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>Est supprimé</p></td> 
   <td><p>Standard</p></td> 
   <td><p> x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>Site Internet</p></td> 
   <td><p>Standard</p></td> 
   <td><p> x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>Société</p></td> 
   <td><p>Standard</p></td> 
   <td><p> x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>Type</p></td> 
   <td><p>Standard</p></td> 
   <td><p> x</p></td> 
   <td><br></td> 
  </tr> 
 </tbody> 
</table>

**Membre de la campagne**

<table> 
 <tbody> 
  <tr> 
   <th><p>Champs</p></th> 
   <th><p>Standard/Personnalisé</p></th> 
   <th><p>Lecture</p></th> 
   <th><p>Write</p></th> 
  </tr> 
  <tr> 
   <td><p>ID</p></td> 
   <td><p>Standard</p></td> 
   <td><p> x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>Date de création</p></td> 
   <td><p>Standard</p></td> 
   <td><p> x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>LastModifiedDate</p></td> 
   <td><p>Standard</p></td> 
   <td><p> x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>Est supprimé</p></td> 
   <td><p>Standard</p></td> 
   <td><p> x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>FirstRespondedDate</p></td> 
   <td><p>Standard</p></td> 
   <td><p> x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>HasResponded</p></td> 
   <td><p>Standard</p></td> 
   <td><p> x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>IdContact</p></td> 
   <td><p>Standard</p></td> 
   <td><p> x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>LeadId</p></td> 
   <td><p>Standard</p></td> 
   <td><p> x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>IsConverted</p></td> 
   <td><p>Standard</p></td> 
   <td><p> x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>CampaignId</p></td> 
   <td><p>Standard</p></td> 
   <td><p> x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Bizible_Touchpoint_Date__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Touchpoint_Status_Date__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Touchpoint_Status_Contact__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Touchpoint_Status_Leade__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Touchpoint_Status_Opportunity__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x </p></td> 
  </tr> 
 </tbody> 
</table>

## [!DNL Marketo Measure] Objets personnalisés dans [!DNL Salesforce] {#marketo-measure-custom-objects-in-salesforce}

Outre la création de champs personnalisés sur les objets standard de la collecte de données régionale, une fois que la variable [!DNL Marketo Measure] est installé, il crée quelques objets personnalisés. Vous trouverez ci-dessous une liste de ces objets personnalisés, ainsi qu’un tableau indiquant les champs qui [!DNL Marketo Measure] écrira sur .

**Point de contact de l&#39;acheteur**

Le point de contact de l’acheteur est un [!DNL Marketo Measure] Objet personnalisé pour encapsuler les interactions marketing pour les contacts, les pistes et les cas.

<table> 
 <tbody> 
  <tr> 
   <th><p>Champs</p></th> 
   <th><p>Standard/Personnalisé</p></th> 
   <th><p>Lecture</p></th> 
   <th><p>Write</p></th> 
  </tr> 
  <tr> 
   <td><p>bizible2__Bizible_Person__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__SF_Campaign__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__UniqueId__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Marketing_Channel__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Marketing_Channel_Path__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Touchpoint_Type__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Ad_Id__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Ad_Content__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Ad_Group_Id__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Ad_Group_Name__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Ad_Campaign_Id__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Ad_Campaign_Name__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Placement_Id__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Placement_Name__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Site_Id__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Site_Name__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Form_URL__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Form_URL_Raw__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Platform__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Browser__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Geo_City__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Geo_Country__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Geo_Region__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Keyword_Id__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Keyword_MatchType__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Touchpoint_Position__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Keyword_Text__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Landing_Page__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Landing_Page_Raw__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Medium__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Referrer_Page__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Referrer_Page_Raw__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Search_Expression__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Touchpoint_Date__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Touchpoint_Source__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Segment__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Count_First_Touch__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Count_Lead_Creation_Touch__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Count_U_Shaped__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Ad_Destination_URL__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Case__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Contact__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
 </tbody> 
</table>

**[!DNL Marketo Measure]Individu**

La variable [!DNL Marketo Measure] La personne est une [!DNL Marketo Measure] Objet personnalisé relatif aux objets de piste, de contact et de cas.

<table> 
 <tbody> 
  <tr> 
   <th><p>Champs</p></th> 
   <th><p>Standard/Personnalisé</p></th> 
   <th><p>Lecture</p></th> 
   <th><p>Write</p></th> 
  </tr> 
  <tr> 
   <td><p>bizible2__UniqueId__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Lead__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Case__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Contact__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x </p></td> 
  </tr> 
 </tbody> 
</table>

## Point de contact d’attribution de l’achat {#buyer-attribution-touchpoint}

Le point de contact d’attribution de l’achat est un [!DNL Marketo Measure] Objet personnalisé pour encapsuler l’influence du marketing sur les opportunités.

**Point de contact d’attribution de l’achat**

<table> 
 <tbody> 
  <tr> 
   <th><p>Champs</p></th> 
   <th><p>Standard/Personnalisé</p></th> 
   <th><p>Lecture</p></th> 
   <th><p>Write</p></th> 
  </tr> 
  <tr> 
   <td><p>bizible2__Account__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__SF_Campaign__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Contact__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Opportunity__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__UniqueId__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Marketing_Channel__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Marketing_Channel_Path__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Touchpoint_Type__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Ad_Id__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Ad_Content__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Ad_Group_Id__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Ad_Group_Name__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Ad_Campaign_Id__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Ad_Campaign_Name__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Placement_Id__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Placement_Name__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Site_Id__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Site_Name__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Form_URL__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Form_URL_Raw__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Platform__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Browser__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Geo_City__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Geo_Country__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Geo_Region__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Keyword_Id__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Keyword_MatchType__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Touchpoint_Position__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Keyword_Text__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Landing_Page__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Landing_Page_Raw__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Medium__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Referrer_Page__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Referrer_Page_Raw__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Search_Expression__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Touchpoint_Date__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Touchpoint_Source__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Segment__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Attribution_First_Touch__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Attribution_Lead_Conversion_Touch__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Attribution_U_Shaped__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Attribution_W_Shaped__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Attribution_Custom_Model__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Attribution_Custom_Model_2__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Count_First_Touch__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Count_Lead_Creation_Touch__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Count_U_Shaped__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Count_W_Shaped__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Count_Custom_Model__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Count_Custom_Model_2__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Ad_Destination_URL__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Revenue_First_Touch__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Revenue_Lead_Creation_Touch__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Revenue_U_Shaped__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Revenue_W_Shaped__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Revenue_Custom_Model__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Revenue_Custom_Model_2__c</p></td> 
   <td><p>Personnaliser</p></td> 
   <td><p> x</p></td> 
   <td><p> x</p></td> 
  </tr> 
 </tbody> 
</table>
