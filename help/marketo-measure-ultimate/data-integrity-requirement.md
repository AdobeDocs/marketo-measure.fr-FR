---
description: '[!DNL Marketo Measure] Exigence ultime d’intégrité des données - [!DNL Marketo Measure]'
title: « Exigence en matière d’intégrité des données [!DNL Marketo Measure] Ultimate »
feature: Integration, Tracking, Attribution
exl-id: 8ad001d0-e9fe-46f5-b808-d6203a55a229
source-git-commit: 54695bd795fe9bdb58d97b6b0762b9e9fe8f17cf
workflow-type: tm+mt
source-wordcount: '1611'
ht-degree: 86%

---

# Exigence en matière d’intégrité des données [!DNL Marketo Measure] Ultimate {#marketo-measure-ultimate-data-integrity-requirement}

[!DNL Marketo Measure] valide les jeux de données AEP entrants pour s’assurer que les données sont suffisantes et cohérentes pour l’attribution. Si vous ne remplissez pas les exigences d’intégrité des données, le jeu de données est rejeté par le système [!DNL Marketo Measure]. Cet article décrit les exigences en matière d’intégrité des données, fournit des exemples de requête pour l’inspection des données et recommande une solution pour les champs obligatoires avec une valeur nulle.

## Objet d’entité {#entity-object}

<table style="table-layout:auto">
  <tr>
    <th>Classe XDM</th>
    <th>Groupe de champs XDM</th>
    <th>Chemin XDM</th>
    <th>Type XDM</th>
    <th>Champ de source de données</th>
    <th>Obligatoire ?</th>
    <th>Notes</th>
  </tr>
  <tbody>
    <tr>
      <td colspan="7"><strong>Compte</strong> (compte pour Salesforce, entreprise et/ou compte nommé pour Marketo)</td>
    </tr>
    <tr>
      <td rowspan="6">Compte professionnel XDM</td>
      <td></td>
      <td>accountKey.sourceKey</td>
      <td>Chaîne</td>
      <td></td>
      <td>Oui</td>
      <td>Par exemple : 123@999-abc-888.Marketo</td>
    </tr>
    <tr>
      <td></td>
      <td>accountKey.sourceID</td>
      <td>Chaîne</td>
      <td>ID</td>
      <td>Oui</td>
      <td>Par exemple : 123</td>
    </tr>
    <tr>
      <td></td>
      <td>accountKey.sourceInstanceID</td>
      <td>Chaîne</td>
      <td></td>
      <td>Oui</td>
      <td>Par exemple : 999-abc-888</td>
    </tr>
    <tr>
      <td></td>
      <td>accountKey.sourceType</td>
      <td>Chaîne</td>
      <td></td>
      <td>Oui</td>
      <td>Par exemple : Marketo</td>
    </tr>
    <tr>
      <td></td>
      <td>extSourceSystemAudit.createdDate</td>
      <td>Date-heure</td>
      <td>Date de création</td>
      <td>Oui</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td>extSourceSystemAudit.lastUpdatedDate</td>
      <td>Date-heure</td>
      <td>Date de modification</td>
      <td>Oui</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td>Détails du compte professionnel XDM</td>
      <td>accountName</td>
      <td>Chaîne</td>
      <td>Nom</td>
      <td>Oui</td>
      <td></td>
    </tr>
    <tr>
      <td colspan="7"><strong>Campagne</strong> (campagne pour Salesforce, programme pour Marketo)</td>
    </tr>
    <tr>
      <td rowspan="8">Campagne commerciale XDM</td>
      <td></td>
      <td>campaignKey.sourceKey</td>
      <td>Chaîne</td>
      <td></td>
      <td>Oui</td>
      <td>Par exemple : 55555@999-abc-888.Marketo</td>
    </tr>
    <tr>
      <td></td>
      <td>campaignKey.sourceID</td>
      <td>Chaîne</td>
      <td>ID</td>
      <td>Oui</td>
      <td>Par exemple : 55555</td>
    </tr>
    <tr>
      <td></td>
      <td>campaignKey.sourceInstanceID</td>
      <td>Chaîne</td>
      <td></td>
      <td>Oui</td>
      <td>Par exemple : 999-abc-888</td>
    </tr>
    <tr>
      <td></td>
      <td>campaignKey.sourceType</td>
      <td>Chaîne</td>
      <td></td>
      <td>Oui</td>
      <td>Par exemple : Marketo</td>
    </tr>
    <tr>
      <td></td>
      <td>extSourceSystemAudit.createdDate</td>
      <td>Date-heure</td>
      <td>Date de création</td>
      <td>Oui</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td>extSourceSystemAudit.lastUpdatedDate</td>
      <td>Date-heure</td>
      <td>Date de modification</td>
      <td>Oui</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td>Nom de campagne</td>
      <td>Chaîne</td>
      <td>Nom</td>
      <td>Oui</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td>Type de campagne</td>
      <td>Chaîne</td>
      <td>Type de campagne</td>
      <td>Non</td>
      <td>Pour le mappage des canaux</td>
    </tr>
    <tr>
      <td></td>
      <td rowspan="5">Détails des campagnes commerciales XDM</td>
      <td>Nom de canal</td>
      <td>Chaîne</td>
      <td>Nom de canal</td>
      <td>Non</td>
      <td>Pour le mappage des canaux</td>
    </tr>
    <tr>
      <td></td>
      <td>campaignStartDate</td>
      <td>Date-heure</td>
      <td>StartDate</td>
      <td>Non</td>
      <td>Pour le coût de la campagne</td>
    </tr>
    <tr>
      <td></td>
      <td>campaignEndDate</td>
      <td>Date-heure</td>
      <td>EndDate</td>
      <td>Non</td>
      <td>Pour le coût de la campagne</td>
    </tr>
    <tr>
      <td></td>
      <td>actualCost.amount</td>
      <td>Nombre</td>
      <td>Coût</td>
      <td>Non</td>
      <td>Pour le coût de la campagne</td>
    </tr>
    <tr>
      <td></td>
      <td>realCost.currencyCode</td>
      <td>
        <p>Chaîne</p>
        <p>^[A-Z]{3}$</p>
      </td>
      <td>CurrencyIsoCode</td>
      <td>Non</td>
      <td>Pour le coût de la campagne</td>
    </tr>
    <tr>
      <td colspan="7"><strong>Membre de la campagne</strong> (membre de la campagne pour Salesforce, adhésions au programme pour Marketo)</td>
    </tr>
    <tr>
      <td rowspan="14">Membres de la campagne commerciale XDM</td>
      <td></td>
      <td>campaignMemberKey.sourceKey</td>
      <td>Chaîne</td>
      <td></td>
      <td>Oui</td>
      <td>Par exemple : 987654321@999-abc-888.Marketo</td>
    </tr>
    <tr>
      <td></td>
      <td>campaignMemberKey.sourceID</td>
      <td>Chaîne</td>
      <td>ID</td>
      <td>Oui</td>
      <td>Par exemple : 987654321</td>
    </tr>
    <tr>
      <td></td>
      <td>campaignMemberKey.sourceInstanceID</td>
      <td>Chaîne</td>
      <td></td>
      <td>Oui</td>
      <td>Par exemple : 999-abc-888</td>
    </tr>
    <tr>
      <td></td>
      <td>campaignMemberKey.sourceType</td>
      <td>Chaîne</td>
      <td></td>
      <td>Oui</td>
      <td>Par exemple : Marketo</td>
    </tr>
    <tr>
      <td></td>
      <td>extSourceSystemAudit.createdDate</td>
      <td>Date-heure</td>
      <td>Date de création</td>
      <td>Oui</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td>extSourceSystemAudit.lastUpdatedDate</td>
      <td>Date-heure</td>
      <td>Date de modification</td>
      <td>Oui</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td>personKey.sourceKey</td>
      <td>Chaîne</td>
      <td></td>
      <td>Oui</td>
      <td>Par exemple : 333@999-abc-888.Marketo</td>
    </tr>
    <tr>
      <td></td>
      <td>personKey.sourceID</td>
      <td>Chaîne</td>
      <td>ID de lead ou de contact</td>
      <td>Oui</td>
      <td>
        <p>Par exemple : 333 (selon la table de la source de données, il s’agit de l’ID de lead ou de contact).</p>
        <p>Clé étrangère du lead ou du contact</p>
      </td>
    </tr>
    <tr>
      <td></td>
      <td>personKey.sourceInstanceID</td>
      <td>Chaîne</td>
      <td></td>
      <td>Oui</td>
      <td>Par exemple : 999-abc-888</td>
    </tr>
    <tr>
      <td></td>
      <td>personKey.sourceType</td>
      <td>Chaîne</td>
      <td></td>
      <td>Oui</td>
      <td>Par exemple : Marketo</td>
    </tr>
    <tr>
      <td></td>
      <td>campaignKey.sourceKey</td>
      <td>Chaîne</td>
      <td></td>
      <td>Oui</td>
      <td>Par exemple : 55555@999-abc-888.Marketo</td>
    </tr>
    <tr>
      <td></td>
      <td>campaignKey.sourceID</td>
      <td>Chaîne</td>
      <td>ID de la campagne</td>
      <td>Oui</td>
      <td>
        <p>Par exemple : 55555.</p>
        <p>Clé étrangère de la campagne</p>
      </td>
    </tr>
    <tr>
      <td></td>
      <td>campaignKey.sourceInstanceID</td>
      <td>Chaîne</td>
      <td></td>
      <td>Oui</td>
      <td>Par exemple : 999-abc-888</td>
    </tr>
    <tr>
      <td></td>
      <td>campaignKey.sourceType</td>
      <td>Chaîne</td>
      <td></td>
      <td>Oui</td>
      <td>Par exemple : Marketo</td>
    </tr>
    <tr>
      <td></td>
      <td rowspan="4">Détails des membres de la campagne commerciale XDM</td>
      <td>b2b.personType</td>
      <td>Chaîne</td>
      <td>« Lead » ou « contact »</td>
      <td>Oui</td>
      <td>En fonction de la table de la source de données, cette valeur doit être définie sur « Lead » ou « Contact ». Nous vous recommandons de définir cette valeur sur « Contact » pour la plupart des cas d’utilisation</td>
    </tr>
    <tr>
      <td></td>
      <td>memberStatus</td>
      <td>Chaîne</td>
      <td>Statut</td>
      <td>Oui</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td>hasResponded</td>
      <td>Booléen</td>
      <td>HasResponded</td>
      <td>Oui</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td>firstRespondedDate</td>
      <td>Date-heure</td>
      <td>FirstRespondedDate</td>
      <td>Non</td>
      <td></td>
    </tr>
    <tr>
      <td colspan="7"><strong>Personne</strong> (contact ou lead pour Salesforce, personnes pour Marketo)</td>
    </tr>
    <tr>
      <td>Profil individuel XDM</td>
      <td rowspan="11">Détails des personnes commerciales XDM</td>
      <td>b2b.personKey.sourceKey</td>
      <td>Chaîne</td>
      <td></td>
      <td>Oui</td>
      <td>Par exemple : 333@999-abc-888.Marketo</td>
    </tr>
    <tr>
      <td></td>
      <td>b2b.personKey.sourceID</td>
      <td>Chaîne</td>
      <td>ID</td>
      <td>Oui</td>
      <td>Par exemple : 333, selon la table de la source de données, il s’agit de l’ID de piste ou de contact.</td>
    </tr>
    <tr>
      <td></td>
      <td>b2b.personKey.sourceInstanceID</td>
      <td>Chaîne</td>
      <td></td>
      <td>Oui</td>
      <td>Par exemple : 999-abc-888</td>
    </tr>
    <tr>
      <td></td>
      <td>b2b.personKey.sourceType</td>
      <td>Chaîne</td>
      <td></td>
      <td>Oui</td>
      <td>Par exemple : Marketo</td>
    </tr>
    <tr>
      <td></td>
      <td>workEmail.address</td>
      <td>
        <p>Chaîne</p>
        <p>E-mail</p>
      </td>
      <td>E-mail</td>
      <td>Oui</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td>b2b.personStatus</td>
      <td>Chaîne</td>
      <td>Statut</td>
      <td><b><i>Oui pour le type de personne « Lead » uniquement</i></b></td>
      <td>Obligatoire uniquement si b2b.personType est « Lead »</td>
    </tr>
    <tr>
      <td></td>
      <td>extSourceSystemAudit.createdDate</td>
      <td>Date-heure</td>
      <td>Date de création</td>
      <td>Oui</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td>extSourceSystemAudit.lastUpdatedDate</td>
      <td>Date-heure</td>
      <td>Date de modification</td>
      <td>Oui</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td>b2b.isConverted</td>
      <td>Booléen</td>
      <td>IsConverted</td>
      <td><b><i>Oui pour le type de personne « Lead » uniquement</i></b></td>
      <td>Obligatoire uniquement si b2b.personType est « Lead »</td>
    </tr>
    <tr>
      <td></td>
      <td>b2b.personType</td>
      <td>Chaîne</td>
      <td>« Lead » ou « contact »</td>
      <td>Oui</td>
      <td>En fonction de la table de la source de données, cette valeur doit être définie sur « Lead » ou « Contact ». Nous vous recommandons de définir cette valeur sur « Contact » pour la plupart des cas d’utilisation</td>
    </tr>
    <tr>
      <td></td>
      <td>extendedWorkDetails.jobTitle</td>
      <td>Chaîne</td>
      <td></td>
      <td>Non</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td rowspan="4">Composants de personnes commerciales XDM</td>
      <td>personComponents.sourceAccountKey.sourceKey</td>
      <td>Chaîne</td>
      <td></td>
      <td>Non</td>
      <td>
        <p>Par exemple : 123@999-abc-888.Marketo.</p>
        <p>Les champs sourceAccountKey ne sont « obligatoires » que pour les véritables enregistrements de contacts, définis comme des enregistrements de personnes liés au compte. S’ils ne sont pas renseignés, le jeu de données n’est pas rejeté, mais les résultats de l’attribution seront incorrects.</p>
        <p>personComponents est un tableau, mais Marketo Measure utilise uniquement le premier élément personComponents[0]</p>
      </td>
    </tr>
    <tr>
      <td></td>
      <td>personComponents.sourceAccountKey.sourceID</td>
      <td>Chaîne</td>
      <td>Identifiant de compte</td>
      <td>Non</td>
      <td>
        <p>Par exemple : 123.</p>
        <p>Clé étrangère du compte</p>
      </td>
    </tr>
    <tr>
      <td></td>
      <td>personComponents.sourceAccountKey.sourceInstanceID</td>
      <td>Chaîne</td>
      <td></td>
      <td>Non</td>
      <td>Par exemple : 999-abc-888</td>
    </tr>
    <tr>
      <td></td>
      <td>personComponents.sourceAccountKey.sourceType</td>
      <td>Chaîne</td>
      <td></td>
      <td>Non</td>
      <td>Par exemple : Marketo</td>
    </tr>
    <tr>
      <td colspan="7"><strong>Opportunité</strong> (opportunité pour Salesforce, opportunités pour Marketo)</td>
    </tr>
    <tr>
      <td rowspan="13">Opportunités commerciales XDM</td>
      <td></td>
      <td>opportunityKey.sourceKey</td>
      <td>Chaîne</td>
      <td></td>
      <td>Oui</td>
      <td>Par exemple : 77777@999-abc-888.Marketo</td>
    </tr>
    <tr>
      <td></td>
      <td>opportunityKey.sourceID</td>
      <td>Chaîne</td>
      <td>ID</td>
      <td>Oui</td>
      <td>Par exemple : 77777</td>
    </tr>
    <tr>
      <td></td>
      <td>opportunityKey.sourceInstanceID</td>
      <td>Chaîne</td>
      <td></td>
      <td>Oui</td>
      <td>Par exemple : 999-abc-888</td>
    </tr>
    <tr>
      <td></td>
      <td>opportunityKey.sourceType</td>
      <td>Chaîne</td>
      <td></td>
      <td>Oui</td>
      <td>Par exemple : Marketo</td>
    </tr>
    <tr>
      <td></td>
      <td>extSourceSystemAudit.createdDate</td>
      <td>Date-heure</td>
      <td>Date de création</td>
      <td>Oui</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td>extSourceSystemAudit.lastUpdatedDate</td>
      <td>Date-heure</td>
      <td>Date de modification</td>
      <td>Oui</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td>accountKey.sourceKey</td>
      <td>Chaîne</td>
      <td></td>
      <td>Oui</td>
      <td>Par exemple : 123@999-abc-888.Marketo</td>
    </tr>
    <tr>
      <td></td>
      <td>accountKey.sourceID</td>
      <td>Chaîne</td>
      <td>Identifiant de compte</td>
      <td>Oui</td>
      <td>
        <p>Par exemple : 123.</p>
        <p>Clé étrangère du compte</p>
      </td>
    </tr>
    <tr>
      <td></td>
      <td>accountKey.sourceInstanceID</td>
      <td>Chaîne</td>
      <td></td>
      <td>Oui</td>
      <td>Par exemple : 999-abc-888</td>
    </tr>
    <tr>
      <td></td>
      <td>accountKey.sourceType</td>
      <td>Chaîne</td>
      <td></td>
      <td>Oui</td>
      <td>Par exemple : Marketo</td>
    </tr>
    <tr>
      <td></td>
      <td>opportunityName</td>
      <td>Chaîne</td>
      <td>Nom</td>
      <td>Oui</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td>opportunityStage</td>
      <td>Chaîne</td>
      <td>Étape</td>
      <td>Oui</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td>opportunityType</td>
      <td>Chaîne</td>
      <td></td>
      <td>Non</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td rowspan="5">Détails des opportunités commerciales XDM</td>
      <td>isWon</td>
      <td>Booléen</td>
      <td>IsWon</td>
      <td>Oui</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td>isClosed</td>
      <td>Booléen</td>
      <td>IsClosed</td>
      <td>Oui</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td>expectedCloseDate</td>
      <td>Date</td>
      <td>CloseDate</td>
      <td>Oui</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td>opportunityAmount.amount</td>
      <td>Nombre</td>
      <td>Montant</td>
      <td>Oui</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td>opportunityAmount.currencyCode</td>
      <td>
        <p>Chaîne</p>
        <p>^[A-Z]{3}$</p>
      </td>
      <td>CurrencyIsoCode</td>
      <td>Oui</td>
      <td></td>
    </tr>
    <tr>
      <td colspan="7"><strong>Rôle de contact d’opportunité (nécessaire uniquement si vous envisagez d’utiliser le rôle de contact d’opportunité en tant que groupe d’achats pour l’attribution)</strong></td>
    </tr>
    <tr>
      <td rowspan="16">Relation de personne avec les opportunités commerciales XDM</td>
      <td></td>
      <td>personKey.sourceKey</td>
      <td>Chaîne</td>
      <td></td>
      <td>Oui</td>
      <td>Par exemple : 333@999-abc-888.Marketo</td>
    </tr>
    <tr>
      <td></td>
      <td>personKey.sourceID</td>
      <td>Chaîne</td>
      <td>ID du contact</td>
      <td>Oui</td>
      <td>
        <p>Par exemple : 333.</p>
        <p>Clé étrangère du contact</p>
      </td>
    </tr>
    <tr>
      <td></td>
      <td>personKey.sourceInstanceID</td>
      <td>Chaîne</td>
      <td></td>
      <td>Oui</td>
      <td>Par exemple : 999-abc-888</td>
    </tr>
    <tr>
      <td></td>
      <td>personKey.sourceType</td>
      <td>Chaîne</td>
      <td></td>
      <td>Oui</td>
      <td>Par exemple : Marketo</td>
    </tr>
    <tr>
      <td></td>
      <td>isPrimary</td>
      <td>Booléen</td>
      <td>IsPrimary</td>
      <td>Oui</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td>opportunityKey.sourceKey</td>
      <td>Chaîne</td>
      <td></td>
      <td>Oui</td>
      <td>Par exemple : 77777@999-abc-888.Marketo</td>
    </tr>
    <tr>
      <td></td>
      <td>opportunityKey.sourceID</td>
      <td>Chaîne</td>
      <td>ID de l’opportunité</td>
      <td>Oui</td>
      <td>
        <p>Par exemple : 77777.</p>
        <p>Clé étrangère de l’opportunité</p>
      </td>
    </tr>
    <tr>
      <td></td>
      <td>opportunityKey.sourceInstanceID</td>
      <td>Chaîne</td>
      <td></td>
      <td>Oui</td>
      <td>Par exemple : 999-abc-888</td>
    </tr>
    <tr>
      <td></td>
      <td>opportunityKey.sourceType</td>
      <td>Chaîne</td>
      <td></td>
      <td>Oui</td>
      <td>Par exemple : Marketo</td>
    </tr>
    <tr>
      <td></td>
      <td>opportunityPersonKey.sourceKey</td>
      <td>Chaîne</td>
      <td></td>
      <td>Oui</td>
      <td>Par exemple : 222222@999-abc-888.Marketo</td>
    </tr>
    <tr>
      <td></td>
      <td>opportunityPersonKey.sourceID</td>
      <td>Chaîne</td>
      <td>ID</td>
      <td>Oui</td>
      <td>Par exemple : 222222</td>
    </tr>
    <tr>
      <td></td>
      <td>opportunityPersonKey.sourceInstanceID</td>
      <td>Chaîne</td>
      <td></td>
      <td>Oui</td>
      <td>Par exemple : 999-abc-888</td>
    </tr>
    <tr>
      <td></td>
      <td>opportunityPersonKey.sourceType</td>
      <td>Chaîne</td>
      <td></td>
      <td>Oui</td>
      <td>Par exemple : Marketo</td>
    </tr>
    <tr>
      <td></td>
      <td>personRole</td>
      <td>Chaîne</td>
      <td>Rôle</td>
      <td>Non</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td>extSourceSystemAudit.createdDate</td>
      <td>Date-heure</td>
      <td>Date de création</td>
      <td>Oui</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td>extSourceSystemAudit.lastUpdatedDate</td>
      <td>Date-heure</td>
      <td>Date de modification</td>
      <td>Oui</td>
      <td></td>
    </tr>
    <tr>
      <td colspan="7"><strong>Taux de conversion (nécessaire uniquement si vous utilisez plusieurs devises. Notez qu’un seul jeu de données de taux de conversion peut être activé sur Marketo Measure)</strong></td>
    </tr>
    <tr>
      <td rowspan="7">Conversion</td>
      <td></td>
      <td>extSourceSystemAudit.externalKey.sourceKey</td>
      <td>Chaîne</td>
      <td></td>
      <td>Oui</td>
      <td>Par exemple : 8888@0x012345.Salesforce</td>
    </tr>
    <tr>
      <td></td>
      <td>extSourceSystemAudit.externalKey.sourceId</td>
      <td>Chaîne</td>
      <td>ID</td>
      <td>Oui</td>
      <td>Par exemple : 8888</td>
    </tr>
    <tr>
      <td></td>
      <td>extSourceSystemAudit.externalKey.sourceInstanceId</td>
      <td>Chaîne</td>
      <td></td>
      <td>Oui</td>
      <td>Par exemple : 0x012345</td>
    </tr>
    <tr>
      <td></td>
      <td>extSourceSystemAudit.externalKey.sourceType</td>
      <td>Chaîne</td>
      <td></td>
      <td>Oui</td>
      <td>Par exemple : Salesforce</td>
    </tr>
    <tr>
      <td></td>
      <td>extSourceSystemAudit.createdDate</td>
      <td>Date-heure</td>
      <td>Date de création</td>
      <td>Oui</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td>extSourceSystemAudit.lastUpdatedDate</td>
      <td>Date-heure</td>
      <td>Date de modification</td>
      <td>Oui</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td>isDeleted</td>
      <td>Booléen</td>
      <td></td>
      <td>Oui</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td rowspan="5">Détails du taux de conversion des devises</td>
      <td>conversionRate</td>
      <td>Nombre</td>
      <td>ConversionRate</td>
      <td>Oui</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td>endDate</td>
      <td>Date</td>
      <td>NextStartDate</td>
      <td>Oui</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td>startDate</td>
      <td>Date</td>
      <td>StartDate</td>
      <td>Oui</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td>sourceISOCode</td>
      <td>Chaîne</td>
      <td>ISOCode</td>
      <td>Oui</td>
      <td>Par exemple : EUR</td>
    </tr>
    <tr>
      <td></td>
      <td>targetISOCode</td>
      <td>Chaîne</td>
      <td></td>
      <td>Oui</td>
      <td>Code de devise par défaut défini dans Marketo Measure. Par exemple : USD.</td>
    </tr>
  </tbody>
</table>

## Exigences de données de conversion de devise {#currency-conversion-data-requirements}

**Devise par défaut** : dans Marketo Measure, toutes les recettes et tous les coûts sont convertis en devise par défaut au moment de la création du rapport. Il doit y avoir un enregistrement avec la même couverture de date pour la devise cible elle-même (par exemple, USD vers USD) avec un taux de conversion de 1.

**Taux de conversion** : chaque paire (devise source, devise cible) peut avoir plusieurs taux de conversion pour différentes périodes. Les taux doivent couvrir toute la durée de 0001-01-01 à 9999-12-31, selon l’objet Salesforce DatedConversionRate .

**Plage de dates** :
* Aucune période ne chevauche un jeu de taux (devise source, devise cible) (par exemple, 2023-01-01 à 2023-02-01 et 2023-01-01 à 2024-01-01).
* Aucun intervalle entre les périodes. La date de début est incluse et la date de fin est exclusive.

<p>

## ExperienceEvent {#experienceevent}

<table style="table-layout:auto">
  <tr>
    <th>Classe XDM</th>
    <th>Groupe de champs XDM</th>
    <th>Chemin XDM</th>
    <th>Type XDM</th>
    <th>Champ de source de données</th>
    <th>Obligatoire ?</th>
    <th>Notes</th>
  </tr>
  <tbody>
    <tr>
      <td colspan="7"><strong>Activité</strong></td>
    </tr>
    <tr>
      <td rowspan="3">XDM ExperienceEvent</td>
      <td></td>
      <td>_id</td>
      <td>Chaîne</td>
      <td>ID</td>
      <td>Oui</td>
      <td>Oui</td>
    </tr>
    <tr>
      <td></td>
      <td>eventType</td>
      <td>Chaîne</td>
      <td>Type d’activité</td>
      <td>Oui</td>
      <td>Oui</td>
    </tr>
    <tr>
      <td></td>
      <td>Date et heure</td>
      <td>Date-heure</td>
      <td>Date de l’activité</td>
      <td>Oui</td>
      <td>Oui</td>
    </tr>
    <tr>
      <td></td>
      <td>Identifiant de personne</td>
      <td>personKey.sourceKey</td>
      <td>Chaîne</td>
      <td></td>
      <td>Oui</td>
      <td>Par exemple : 333@999-abc-888.Marketo</td>
    </tr>
    <tr>
      <td></td>
      <td></td>
      <td>personKey.sourceID</td>
      <td>Chaîne</td>
      <td>ID de lead ou de contact</td>
      <td>Oui</td>
      <td>
        <p>Par exemple : 333 (selon la table de la source de données, il s’agit de l’ID de lead ou de contact).</p>
        <p>Clé étrangère du lead ou du contact</p>
      </td>
    </tr>
    <tr>
      <td></td>
      <td></td>
      <td>personKey.sourceInstanceID</td>
      <td>Chaîne</td>
      <td></td>
      <td>Oui</td>
      <td>Par exemple : 999-abc-888</td>
    </tr>
    <tr>
      <td></td>
      <td></td>
      <td>personKey.sourceType</td>
      <td>Chaîne</td>
      <td></td>
      <td>Oui</td>
      <td>Par exemple : Marketo</td>
    </tr>
    <tr>
      <td></td>
      <td>Ajouter à la campagne</td>
      <td>leadOperation.addToCampaign.campaignKey.sourceKey</td>
      <td>Chaîne</td>
      <td></td>
      <td>Oui pour le type leadOperation.addToCampaign uniquement</td>
      <td>Par exemple : 55555@999-abc-888.Marketo</td>
    </tr>
    <tr>
      <td></td>
      <td></td>
      <td>leadOperation.addToCampaign.campaignKey.sourceId</td>
      <td>Chaîne</td>
      <td>ID de la campagne</td>
      <td>Oui pour le type leadOperation.addToCampaign uniquement</td>
      <td>
        <p>Par exemple : 55555.</p>
        <p>Clé étrangère de la campagne</p>
      </td>
    </tr>
    <tr>
      <td></td>
      <td></td>
      <td>leadOperation.addToCampaign.campaignKey.sourceInstanceId</td>
      <td>Chaîne</td>
      <td></td>
      <td>Oui pour le type leadOperation.addToCampaign uniquement</td>
      <td>Par exemple : 999-abc-888</td>
    </tr>
    <tr>
      <td></td>
      <td></td>
      <td>leadOperation.addToCampaign.campaignKey.sourceType</td>
      <td>Chaîne</td>
      <td></td>
      <td>Oui pour le type leadOperation.addToCampaign uniquement</td>
      <td>Par exemple : Marketo</td>
    </tr>
    <tr>
      <td></td>
      <td>Statut modifié dans la progression de la campagne</td>
      <td>leadOperation.campaignProgression.campaignKey.sourceKey</td>
      <td>Chaîne</td>
      <td></td>
      <td>Oui pour le type leadOperation.campaignProgression uniquement</td>
      <td>Par exemple : 55555@999-abc-888.Marketo</td>
    </tr>
    <tr>
      <td></td>
      <td></td>
      <td>leadOperation.campaignProgression.campaignKey.sourceId</td>
      <td>Chaîne</td>
      <td>ID de la campagne</td>
      <td>Oui pour le type leadOperation.campaignProgression uniquement</td>
      <td>
        <p>Par exemple : 55555.</p>
        <p>Clé étrangère de la campagne</p>
      </td>
    </tr>
    <tr>
      <td></td>
      <td></td>
      <td>leadOperation.campaignProgression.campaignKey.sourceInstanceId</td>
      <td>Chaîne</td>
      <td></td>
      <td>Oui pour le type leadOperation.campaignProgression uniquement</td>
      <td>Par exemple : 999-abc-888</td>
    </tr>
    <tr>
      <td></td>
      <td></td>
      <td>leadOperation.campaignProgression.campaignKey.sourceType</td>
      <td>Chaîne</td>
      <td></td>
      <td>Oui pour le type leadOperation.campaignProgression uniquement</td>
      <td>Par exemple : Marketo</td>
    </tr>
  </tbody>
</table>

## Type ExperienceEvent pris en charge {#experienceevent-type-supported}

<table style="table-layout:auto">
  <tr>
    <th>Type d’événement</th>
    <th>Type d’événement XDM</th>
    <th>Description</th>
  </tr>
  <tbody>
    <tr>
      <td>Nouveau lead</td>
      <td>leadOperation.newLead</td>
      <td>Permet d’enregistrer la création et les détails d’un nouveau lead marketing</td>
    </tr>
    <tr>
      <td>Lead converti</td>
      <td>leadOperation.convertLead</td>
      <td>Utilisé lorsqu’un lead marketing est converti en contact qualifié par l’équipe commerciale et affecté à une personne commerciale</td>
    </tr>
    <tr>
      <td>Moment intéressant</td>
      <td>leadOperation.interestingMoment</td>
      <td>Utilisé pour le suivi des activités à forte valeur ajoutée par des clientes et clients potentiels</td>
    </tr>
    <tr>
      <td>Remplir formulaire</td>
      <td>web.formFillOut</td>
      <td>Utilisé pour capturer des détails lorsqu’une personne remplit un formulaire sur une page web</td>
    </tr>
    <tr>
      <td>Se désabonner des e-mails</td>
      <td>directMarketing.emailUnsubscribed</td>
      <td>Utilisé pour capturer des détails lorsqu’une personne se désabonne d’un e-mail</td>
    </tr>
    <tr>
      <td>Ouvrir e-mail</td>
      <td>directMarketing.emailOpening</td>
      <td>Utilisé pour capturer des détails lorsqu’une personne ouvre un e-mail marketing</td>
    </tr>
    <tr>
      <td>Cliquer sur e-mail</td>
      <td>directMarketing.emailClicked</td>
      <td>Utilisé pour capturer des détails lorsqu’une personne clique sur un lien dans un e-mail marketing</td>
    </tr>
    <tr>
      <td>Modifier le statut de progression</td>
      <td>leadOperation.statusInCampaignProgressionChanged</td>
      <td>Utilisé pour capturer des détails sur les modifications du statut d’un lead dans une campagne</td>
    </tr>
    <tr>
      <td>Ajouter au programme d’engagement (ajouter à la maturation)</td>
      <td>leadOperation.addToCampaign</td>
      <td>Utilisé pour ajouter une personne à la campagne spécifique.</td>
    </tr>
  </tbody>
</table>

Utilisez le type d’événement « Moment intéressant » pour les types d’événement non pris en charge dans le tableau ci-dessus. Ajoutez un champ personnalisé pour indiquer le sous-type &quot;Moment intéressant&quot;.

## Exemples de requêtes pour l’examen des données {#query-examples-for-data-inspection}

Vous trouverez ci-dessous une liste d’exemples de requête pour examiner les jeux de données ingérés dans le lac de données AEP. Pour les utiliser par rapport à vos jeux de données, remplacez le nom du tableau dans les exemples de requête ci-dessous par le nom réel du tableau du jeu de données.

Toutes les valeurs doivent être égales à 0.

Le champ personType doit contenir des valeurs « Lead » ou « Contact » uniquement et aucune valeur nulle.

Pour tous les enregistrements de personne « Contact », une clé étrangère de compte doit être présente.

Pour les enregistrements de personne « Lead », une clé étrangère de compte n’existe pas et n’est pas obligatoire. Si vous choisissez d’ingérer des enregistrements de personne « Lead » en tant qu’enregistrements de personne « Contact » (ce qui est recommandé), aucune clé étrangère de compte pour ces enregistrements de personne n’est requise.

### Compte professionnel XDM {#xdm-business-account}

```
select 'account source id', count(*) from salesforce_account where accountKey.sourceId is null
union all
select 'account source type', count(*) from salesforce_account where accountKey.sourceType is null
union all
select 'account source instance id', count(*) from salesforce_account where accountKey.sourceInstanceId is null
union all
select 'account source key', count(*) from salesforce_account where accountKey.sourceKey is null
union all
select 'account name', count(*) from salesforce_account where accountName is null
union all
select 'created date', count(*) from salesforce_account where extSourceSystemAudit.createdDate is null
union all
select 'last updated date', count(*) from salesforce_account where extSourceSystemAudit.lastUpdatedDate is null;
```

### Campagne commerciale XDM {#xdm-business-campaign}

```
select 'campaign source id', count(*) from salesforce_campaign where campaignKey.sourceId is null
union all
select 'campaign source type', count(*) from salesforce_campaign where campaignKey.sourceType is null
union all
select 'campaign source instance id', count(*) from salesforce_campaign where campaignKey.sourceInstanceId is null
union all
select 'campaign source key', count(*) from salesforce_campaign where campaignKey.sourceKey is null
union all
select 'campaign name', count(*) from salesforce_campaign where campaignName is null
union all
select 'created date', count(*) from salesforce_campaign where extSourceSystemAudit.createdDate is null
union all
select 'last updated date', count(*) from salesforce_campaign where extSourceSystemAudit.lastUpdatedDate is null;
```

### Membre de la campagne commerciale XDM {#xdm-business-campaign-member}

```
select 'campaign member source id', count(*) from salesforce_campaign_member where campaignMemberKey.sourceId is null
union all
select 'campaign member source type', count(*) from salesforce_campaign_member where campaignMemberKey.sourceType is null
union all
select 'campaign member source instance id', count(*) from salesforce_campaign_member where campaignMemberKey.sourceInstanceId is null
union all
select 'campaign member source key', count(*) from salesforce_campaign_member where campaignMemberKey.sourceKey is null
union all
select 'campaign source id', count(*) from salesforce_campaign_member where campaignKey.sourceId is null
union all
select 'campaign source type', count(*) from salesforce_campaign_member where campaignKey.sourceType is null
union all
select 'campaign source instance id', count(*) from salesforce_campaign_member where campaignKey.sourceInstanceId is null
union all
select 'campaign source key', count(*) from salesforce_campaign_member where campaignKey.sourceKey is null
union all
select 'person source id', count(*) from salesforce_campaign_member where personKey.sourceId is null
union all
select 'person source type', count(*) from salesforce_campaign_member where personKey.sourceType is null
union all
select 'person source instance id', count(*) from salesforce_campaign_member where personKey.sourceInstanceId is null
union all
select 'person source key', count(*) from salesforce_campaign_member where personKey.sourceKey is null
union all
select distinct 'person type', b2b.personType from salesforce_campaign_member
union all
select 'member status', count(*) from salesforce_campaign_member where memberStatus is null
union all
select 'has responded', count(*) from salesforce_campaign_member where hasResponded is null
union all
select 'created date', count(*) from salesforce_campaign_member where extSourceSystemAudit.createdDate is null
union all
select 'last updated date', count(*) from salesforce_campaign_member where extSourceSystemAudit.lastUpdatedDate is null;
```

### Personne commerciale XDM {#xdm-business-person}

```
select 'person source id', count(*) from marketo_person where b2b.personKey.sourceId is null
union all
select 'person source type', count(*) from marketo_person where b2b.personKey.sourceType is null
union all
select 'person source instance id', count(*) from marketo_person where b2b.personKey.sourceInstanceId is null
union all
select 'person source key', count(*) from marketo_person where b2b.personKey.sourceKey is null
union all
select 'email', count(*) from marketo_person where workEmail.address is null
union all
select 'Lead - person status', count(*) from marketo_person where b2b.personType = 'Lead' and b2b.personStatus is null
union all
select 'Lead - is converted', count(*) from marketo_person where b2b.personType = 'Lead' and b2b.isConverted is null
union all
select distinct 'person type', b2b.personType from marketo_person
union all
select 'created date', count(*) from marketo_person where extSourceSystemAudit.createdDate is null
union all
select 'last updated date', count(*) from marketo_person where extSourceSystemAudit.lastUpdatedDate is null;
```

```
select 'person source id', count(*) from salesforce_contact where b2b.personKey.sourceId is null
union all
select 'person source type', count(*) from salesforce_contact where b2b.personKey.sourceType is null
union all
select 'person source instance id', count(*) from salesforce_contact where b2b.personKey.sourceInstanceId is null
union all
select 'person source key', count(*) from salesforce_contact where b2b.personKey.sourceKey is null
union all
select 'email', count(*) from salesforce_contact where workEmail.address is null
union all
select 'Lead - person status', count(*) from salesforce_contact where b2b.personType = 'Lead' and b2b.personStatus is null
union all
select 'Lead - is converted', count(*) from salesforce_contact where b2b.personType = 'Lead' and b2b.isConverted is null
union all
select distinct 'person type', b2b.personType from salesforce_contact
union all
select 'account source id', count(*) from salesforce_contact where b2b.personType = 'Contact' and personComponents[0].sourceAccountKey.sourceId is null
union all
select 'account source type', count(*) from salesforce_contact where b2b.personType = 'Contact' and personComponents[0].sourceAccountKey.sourceType is null
union all
select 'account source instance id', count(*) from salesforce_contact where b2b.personType = 'Contact' and personComponents[0].sourceAccountKey.sourceInstanceId is null
union all
select 'account source key', count(*) from salesforce_contact where b2b.personType = 'Contact' and personComponents[0].sourceAccountKey.sourceKey is null
union all
select 'created date', count(*) from salesforce_contact where extSourceSystemAudit.createdDate is null
union all
select 'last updated date', count(*) from salesforce_contact where extSourceSystemAudit.lastUpdatedDate is null;
```

### Opportunités commerciales XDM {#xdm-business-opportunity}

```
select 'opportunity source id', count(*) from salesforce_opportunity where opportunityKey.sourceId is null
union all
select 'opportunity source type', count(*) from salesforce_opportunity where opportunityKey.sourceType is null
union all
select 'opportunity source instance id', count(*) from salesforce_opportunity where opportunityKey.sourceInstanceId is null
union all
select 'opportunity source key', count(*) from salesforce_opportunity where opportunityKey.sourceKey is null
union all
select 'account source id', count(*) from salesforce_opportunity where accountKey.sourceId is null
union all
select 'account source type', count(*) from salesforce_opportunity where accountKey.sourceType is null
union all
select 'account source instance id', count(*) from salesforce_opportunity where accountKey.sourceInstanceId is null
union all
select 'account source key', count(*) from salesforce_opportunity where accountKey.sourceKey is null
union all
select 'opportunity name', count(*) from salesforce_opportunity where opportunityName is null
union all
select 'opportunity stage', count(*) from salesforce_opportunity where opportunityStage is null
union all
select 'is won', count(*) from salesforce_opportunity where isWon is null
union all
select 'is closed', count(*) from salesforce_opportunity where isClosed is null
union all
select 'expected close date', count(*) from salesforce_opportunity where expectedCloseDate is null
union all
select 'opportunity amount', count(*) from salesforce_opportunity where opportunityAmount.amount is null
union all
select 'currency code', count(*) from salesforce_opportunity where opportunityAmount.currencyCode is null
union all
select 'created date', count(*) from salesforce_opportunity where extSourceSystemAudit.createdDate is null
union all
select 'last updated date', count(*) from salesforce_opportunity where extSourceSystemAudit.lastUpdatedDate is null;
```

### XDM ExperienceEvent {#xdm-experienceevent}

```
select 'id', count(*) from marketo_activity where _id is null
union all
select 'event type', count(*) from marketo_activity where eventType is null
union all
select 'timestamp', count(*) from marketo_activity where timestamp is null
union all
select 'person source id', count(*) from marketo_activity where personKey.sourceId is null
union all
select 'person source type', count(*) from marketo_activity where personKey.sourceType is null
union all
select 'person source instance id', count(*) from marketo_activity where personKey.sourceInstanceId is null
union all
select 'person source key', count(*) from marketo_activity where personKey.sourceKey is null
union all
select 'addToCampaign campaign id', count(*) from marketo_activity where eventType = 'leadOperation.addToCampaign' and leadOperation.addToCampaign.campaignKey.sourceId is null
union all
select 'addToCampaign campaign type', count(*) from marketo_activity where eventType = 'leadOperation.addToCampaign' and leadOperation.addToCampaign.campaignKey.sourceType is null
union all
select 'addToCampaign campaign instance id', count(*) from marketo_activity where eventType = 'leadOperation.addToCampaign' and leadOperation.addToCampaign.campaignKey.sourceInstanceId is null
union all
select 'addToCampaign campaign key', count(*) from marketo_activity where eventType = 'leadOperation.addToCampaign' and leadOperation.addToCampaign.campaignKey.sourceKey is null
union all
select 'statusInCampaignProgressionChanged campaign id', count(*) from marketo_activity where eventType = 'leadOperation.campaignProgression.campaignKey.sourceKey' and leadOperation.campaignProgression.campaignKey.sourceId is null
union all
select 'statusInCampaignProgressionChanged campaign type', count(*) from marketo_activity where eventType = 'leadOperation.campaignProgression.campaignKey.sourceKey' and leadOperation.campaignProgression.campaignKey.sourceType is null
union all
select 'statusInCampaignProgressionChanged campaign instance id', count(*) from marketo_activity where eventType = 'leadOperation.campaignProgression.campaignKey.sourceKey' and leadOperation.campaignProgression.campaignKey.sourceInstanceId is null
union all
select 'statusInCampaignProgressionChanged campaign key', count(*) from marketo_activity where eventType = 'leadOperation.campaignProgression.campaignKey.sourceKey' and leadOperation.campaignProgression.campaignKey.sourceKey is null;
```

```
select 'id', count(*) from salesforce_task where _id is null
union all
select 'event type', count(*) from salesforce_task where eventType is null
union all
select 'timestamp', count(*) from salesforce_task where timestamp is null
union all
select 'person source id', count(*) from salesforce_task where personKey.sourceId is null
union all
select 'person source type', count(*) from salesforce_task where personKey.sourceType is null
union all
select 'person source instance id', count(*) from salesforce_task where personKey.sourceInstanceId is null
union all
select 'person source key', count(*) from salesforce_task where personKey.sourceKey is null;
```

### Conversion {#conversion}

```
select 'conversion rate', count(*) from currency_conversion_rate where conversionRate is null
union all
select 'end date', count(*) from currency_conversion_rate where endDate is null
union all
select 'start date', count(*) from currency_conversion_rate where startDate is null
union all
select 'source ISO Code', count(*) from currency_conversion_rate where sourceISOCode is null
union all
select 'target ISO Code', count(*) from currency_conversion_rate where targetISOCode is null
union all
select 'source id', count(*) from currency_conversion_rate where extSourceSystemAudit.externalKey.sourceId is null
union all
select 'source type', count(*) from currency_conversion_rate where extSourceSystemAudit.externalKey.sourceType is null
union all
select 'source instance id', count(*) from currency_conversion_rate where extSourceSystemAudit.externalKey.sourceInstanceId is null
union all
select 'source key', count(*) from currency_conversion_rate where extSourceSystemAudit.externalKey.sourceKey is null
union all
select 'created date', count(*) from currency_conversion_rate where extSourceSystemAudit.createdDate is null
union all
select 'last updated date', count(*) from currency_conversion_rate where extSourceSystemAudit.lastUpdatedDate is null;
```

## Solution recommandée pour les champs obligatoires contenant une valeur nulle {#recommended-solution-for-required-fields-with-a-null-value}

Il est recommandé d&#39;utiliser un champ calculé dans le mappage des champs pour définir par défaut le champ sur une valeur non nulle. Voici deux exemples :

* Si la valeur du champ opportunityName de certains enregistrements d’opportunité est nulle, créez le champ calculé suivant et utilisez-le dans le mappage des champs
   * `iif(name != null && trim(name) != "", name, "Unknown")`

* Si leadOperation.campaignProgression.campaignID de certains enregistrements experienceevent est nul, créez le champ calculé suivant et utilisez-le dans le mappage des champs.
   * `iif(leadOperation.campaignProgression.campaignID != null && leadOperation.campaignProgression.campaignID != "" , to_object("sourceType", "Marketo", "sourceInstanceID", "123-abc-321", "sourceID", leadOperation.campaignProgression.campaignID, "sourceKey", concat(leadOperation.campaignProgression.campaignID,"@123-abc-321.Marketo")), iif(eventType == "leadOperation.statusInCampaignProgressionChanged", to_object("sourceType", "Marketo", "sourceInstanceID", "123-abc-321", "sourceID", "Unknown", "sourceKey", "Unknown@123-abc-321.Marketo"), null))`
