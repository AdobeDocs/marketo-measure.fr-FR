---
description: Notifications d’erreur - [!DNL Marketo Measure]
title: Notifications d’erreur
feature: Fundamentals
exl-id: ed07eed6-ddeb-4856-a1ac-ea3d571283f6
source-git-commit: 666812e8bf095170d611cd694b5d0ac5151d8fdd
workflow-type: tm+mt
source-wordcount: '1692'
ht-degree: 30%

---

# Notifications d’erreur {#error-notifications}

Vous trouverez ci-dessous une liste des erreurs que vous pouvez recevoir par notification in-app ou e-mail. Si vous recevez l’un de ces messages, suivez les étapes de dépannage correspondantes. Si ces étapes ne résolvent pas le problème, contactez le [Support de Marketo](https://nation.marketo.com/t5/support/ct-p/Support).

Pour afficher l’intégralité du message de notification dans [!DNL Marketo Measure], cliquez sur **Afficher tout** au bas de l’onglet Notifications .

![](assets/error-notifications-1.png)

<table>
  <tbody>
    <tr>
      <th style="width:31%">Code d’erreur</th>
      <th style="width:23%">Exemple de notification</th>
      <th style="width:23%">Description</th>
      <th style="width:23%">Étapes de dépannage</th>
    </tr>
    <tr>
      <td>API_DISABLED</td>
      <td>Une erreur s’est produite lors de l’import de CRM : API_DISABLED. Les appels API ont été désactivés pour cet utilisateur ou cette utilisatrice.</td>
      <td>L’autorisation d’API a été désactivée pour l’utilisateur ou l’utilisatrice de Marketo Measure.</td>
      <td>Reportez-vous à la documentation Salesforce suivante pour savoir <a href="https://help.salesforce.com/s/articleView?language=en_US&id=sf.branded_apps_commun_api_permset.htm&type=5">comment activer l’accès aux API</a>.</td>
    </tr>
    <tr>
      <td>API_LIMIT_EXCEEDED</td>
      <td>Une erreur s’est produite lors de l’export CRM : PI_LIMIT_EXCEEDED</td>
      <td>La limite de l’API de CRM a été dépassée (24 heures).</td>
      <td>Pour obtenir de l’aide sur l’ajustement des allocations de crédit de l’API, reportez-vous à la documentation suivante pour votre CRM :</p>
          <ul>
            <li><a href="https://learn.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/data-entities/service-protection-monitoring">Dynamics</a>
            </li>
            <li><a href="https://developer.salesforce.com/docs/atlas.en-us.salesforce_app_limits_cheatsheet.meta/salesforce_app_limits_cheatsheet/salesforce_app_limits_platform_api.htm">Salesforce</a>
            </li>
          </ul>
          <p>Vous pouvez également ajuster les crédits CRM utilisés par Marketo Measure en procédant comme suit :</p>
          <ul>
            <li>Accédez à <b>Paramètres</b> &gt; <b>CRM</b> &gt; <b>Général</b>.</li>
            <li>Mettez à jour la limite quotidienne de l’API CRM<br/>.
              <ul>
                <li><b>Remarque : la valeur par défaut est de 100 000.</b></li>
              </ul>
            </li>
          </ul>
          <p>
           <img src="assets/error-notifications-2.png">
          </p>
      </td>
    </tr>
    <tr>
      <td>CANNOT_EXECUTE_FLOW_TRIGGER</td>
      <td>Une erreur s’est produite lors de l’exportation CRM : CANNOT_EXECUTE_FLOW_TRIGGER : type d’entité « Contact ». Donnez ces détails à votre administrateur Salesforce.
Limite dépassée
Vous ou votre organisation avez dépassé la limite maximale pour cette fonctionnalité. ID d'erreur : 123456</td>
      <td>L’enregistrement ne peut pas être enregistré car il ne répond pas à une règle de flux de déclenchement configurée dans l’organisation Salesforce.</td>
      <td>Consultez les détails complets du message de notification et passez en revue les déclencheurs de flux dans l’organisation Salesforce.
La documentation de Salesforce sur les déclencheurs de flux <a href="https://admin.salesforce.com/blog/2023/what-is-a-record-triggered-flow#:~:text=A%20record%2Dtriggered%20flow%20allows,is%20created%20and%2For%20updated">disponible ici</a>.
      </td>
    </tr>
    <tr>
      <td>CANNOT_INSERT_UPDATE_ACTIVATE_ENTITY</td>
      <td>Une erreur s'est produite lors de l'exportation CRM : CANNOT_INSERT_UPDATE_ACTIVATE_ENTITY : Type d'entité 'Lead' : Code d'erreur CRM : CANNOT_INSERT_UPDATE_ACTIVATE_ENTITY, Message d'erreur CRM : System.LimitException : dépassement de la limite de temps Apex CPU, ID d'enregistrement : 0123456.
      <p>
      Une erreur s'est produite lors de l'exportation CRM : CANNOT_INSERT_UPDATE_ACTIVATE_ENTITY : Type d'entité 'Compte' : Code d'erreur CRM : CANNOT_INSERT_UPDATE_ACTIVATE_ENTITY, Message d'erreur CRM : impossible de mettre à jour le type d'entité : Compte, ID d'enregistrement : 0123456</td>
      <td>Les déclencheurs empêchent la mise à jour ou l’insertion d’un objet.
      <p>
      OU
      <p>
      Autorisations manquantes sur l’objet .</td>
      <td>Vérifiez le code de déclencheur entraînant l’échec de l’insertion/la mise à jour. Pour plus d’informations sur les déclencheurs, consultez la documentation Salesforce suivante :
        <ul>
          <li><a href="https://help.salesforce.com/s/articleView?id=sf.code_manage_triggers.htm&type=5">Déclencheurs apex</a>
          </li>
          <li><a href="https://admin.salesforce.com/blog/2023/what-is-a-record-triggered-flow#:~:text=A%20record%2Dtriggered%20flow%20allows,is%20created%20and%2For%20updated"> Déclencheurs de flux </a>
          </li>
        </ul>
        <p>
        Fournissez toutes les autorisations nécessaires à l’utilisateur <a href="/help/configuration-and-setup/marketo-measure-and-salesforce/how-marketo-measure-and-salesforce-interact.md">Marketo Measure</a>.
      </td>
    </tr>
    <tr>
      <td>DUPLICATES_DETECTED</td>
      <td>Une erreur s'est produite lors de l'export CRM : DUPLICATES_DETECTED : Type d'entité 'Contact' : Code d'erreur CRM : DUPLICATES_DETECTED, Message d'erreur CRM : Vous créez un enregistrement en double. Nous vous recommandons d’utiliser plutôt un enregistrement existant., ID d’enregistrement : 0123456</td>
      <td>L’enregistrement importé dans l’organisation Salesforce existe déjà.</td>
      <td><a href="https://help.salesforce.com/s/articleView?id=000390009&type=1">Désactivez le paramètre « Règle en double »</a> pour autoriser les doublons.
          <p>
          Excluez l’utilisateur dédié à Marketo Measure des <a href="https://trailhead.salesforce.com/content/learn/modules/validation-rules/bypass-your-validation-rules"> règles de validation personnalisées </a>.</td>
    </tr>
    <tr>
      <td>DUPLICATE_VALUE</td>
      <td>Une erreur s'est produite lors de l'exportation CRM : DUPLICATE_VALUE : type d'entité 'Lead' : Code d'erreur CRM : DUPLICATE_VALUE, Message d'erreur CRM : valeur en double trouvée : Email_Unique__c duplique la valeur sur l'enregistrement avec l'id : 123, RecordId : 456</td>
      <td>Le champ importé dans l’organisation Salesforce n’autorise pas les valeurs en double.</td>
      <td>Décochez la <a href="https://help.salesforce.com/s/articleView?id=000390009&type=1"> « Case à cocher unique »</a> dans Salesforce.
          <p>
          Excluez l’utilisateur dédié à Marketo Measure des <a href="https://trailhead.salesforce.com/content/learn/modules/validation-rules/bypass-your-validation-rules"> règles de validation personnalisées </a>.</td>
    </tr>
    <tr>
      <td>ENTITY_IS_LOCKED</td>
      <td>Une erreur s'est produite lors de l'export CRM : ENTITY_IS_LOCKED : Type d'entité 'Compte' : Code d'erreur CRM : ENTITY_IS_LOCKED, Message d'erreur CRM : Cet enregistrement est verrouillé. Si vous devez le modifier, contactez votre administrateur., RecordId : 0123456</td>
      <td>Lorsqu’un enregistrement est en cours de processus d’approbation et qu’un utilisateur qui n’est pas l’approbateur actuel ou l’administrateur système tente de le modifier.</td>
      <td>
        <ul>
          <li>Résolvez le processus d’approbation en attente pour cet enregistrement dans l’organisation Salesforce.</li>
          <li>Excluez l’utilisateur dédié à Marketo Measure des <a href="https://trailhead.salesforce.com/content/learn/modules/validation-rules/bypass-your-validation-rules"> règles de validation personnalisées </a>.
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>FIELD_FILTER_VALIDATION_EXCEPTION</td>
      <td>Une erreur s'est produite lors de l'exportation CRM : FIELD_FILTER_VALIDATION_EXCEPTION : Type d'entité 'Lead' : Code d'erreur CRM : FIELD_FILTER_VALIDATION_EXCEPTION, Champ(s) : User__C, Message d'erreur CRM : la valeur n'existe pas ou ne correspond pas aux critères de filtre. Veuillez sélectionner un utilisateur avec le rôle « Chargé de compte, ventes internes » ; ID d’enregistrement : 0123456</td>
      <td>L’enregistrement modifié ne répond plus aux filtres de recherche définis sur l’objet .</td>
      <td>Recherchez des filtres sur l’objet que Marketo Measure tente de modifier. Voir <a href="https://help.salesforce.com/s/articleView?id=000384756&type=1">cet article Salesforce</a> pour savoir comment rechercher des filtres sur un objet.</td>
    </tr>
    <tr>
      <td>FIELD_INTEGRITY_EXCEPTION</td>
      <td>Une erreur s'est produite lors de l'exportation CRM : FIELD_INTEGRITY_EXCEPTION : Type d'entité 'Lead' : Code d'erreur CRM : FIELD_INTEGRITY_EXCEPTION, Champ(s) : Pays, Message d'erreur CRM : Ce pays rencontre un problème, même s'il semble correct. Veuillez sélectionner un pays/territoire dans la liste des pays valides.: Country, RecordId : 0123456</td>
      <td>Le type attendu de l’enregistrement ne correspond pas.</td>
      <td>Le cas le plus courant est celui qui ne suit pas les normes de dénomination des états/pays définies dans l’organisation Salesforce, car les champs des états/pays ont été normalisés pour n’accepter que certaines valeurs de la liste de sélection. Pour résoudre ce problème, vous pouvez :
        <ul>
          <li>Mettez à jour l'enregistrement pour suivre les valeurs acceptées par l'organisation pour ce champ. Contactez votre administrateur SFDC pour obtenir la liste des valeurs acceptées.</li>
          <li><a href="https://help.salesforce.com/s/articleView?id=sf.admin_state_country_picklist_enable.htm&type=5">Désactiver les listes de sélection d’État/pays</a>.
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>INACTIVE_OWNER_OR_USER</td>
      <td>Une erreur s'est produite lors de l'exportation CRM : INACTIVE_OWNER_OR_USER : Type d'entité 'Contact' : Code d'erreur CRM : INACTIVE_OWNER_OR_USER, Message d'erreur CRM : opération effectuée avec l'utilisateur inactif [1234] comme propriétaire du contact, ID d'enregistrement : 0123456</td>
      <td>Il manque l’autorisation « Mettre à jour les enregistrements avec des propriétaires inactifs » dans Marketo Measure.</td>
      <td>Accordez à Marketo Measure l’autorisation « <a href="https://help.salesforce.com/s/articleView?id=000386699&type=1"> Mettre à jour les enregistrements avec des propriétaires inactifs </a> ».</td>
    </tr>
    <tr>
      <td>INSUFFISANT_ACCESS_OR_READONLY</td>
      <td>Une erreur s'est produite lors de l'exportation CRM : INSUFFISANT_ACCESS_OR_READONLY : Type d'entité 'Compte' : Code d'erreur CRM : INSUFFISANT_ACCESS_OR_READONLY, Message d'erreur CRM : droits d'accès insuffisants sur l'ID d'objet : [123], ID d'enregistrement : 456</td>
      <td>Il manque des autorisations sur un objet/champ dans Marketo Measure ou l’objet est en lecture seule.</td>
      <td>Reportez-vous à l’<a href="/help/configuration-and-setup/marketo-measure-and-salesforce/how-marketo-measure-and-salesforce-interact.md">article Experience League suivant</a> pour obtenir des conseils sur les autorisations requises par Marketo Measure.</td>
    </tr>
    <tr>
      <td>INVALID_ADOBE_ANALYTICS_CONFIGURATION</td>
      <td>Une erreur s’est produite lors de l’exportation Adobe Analytics : INVALID_ADOBE_ANALYTICS_CONFIGURATION : erreur : le chargement n’est pas autorisé. Confirmez le schéma de la source de données avant le chargement. ID de la source de données : 1234</td>
      <td>L’intégration d’Adobe Analytics n’est pas configurée correctement.</td>
      <td>Pour garantir une configuration correcte, reportez-vous aux articles d’aide suivants :
        <ul>
          <li>
            <a href="/help/marketo-measure-and-adobe/marketo-measure-integrations-with-adobe-analytics.md">Intégrations de Marketo Measure à Adobe Analytics</a>
          </li>
          <li>
            <a href="https://experienceleague.adobe.com/docs/core-services/interface/services/customer-attributes/t-crs-usecase.html?lang=fr">Création d’une source d’attributs du client et chargement du fichier de données</a>
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>INVALID_CURRENCY_ISO_CODE</td>
      <td>Une erreur s’est produite lors de l’import de l’annonce publicitaire : INVALID_CURRENCY_ISO_CODE. La devise XXX n’est pas prise en charge par Marketo Measure.
      <p>
      Une erreur s’est produite lors de l’import de l’annonce publicitaire : INVALID_CURRENCY_ISO_CODE. La devise XXX sur le compte 1234 n’est pas prise en charge par Marketo Measure.</td>
      <td>Une devise n’est pas prise en charge.</td>
      <td>Dans le système source indiqué dans la notification (Ad, Crm, Marketo), la devise associée à l’enregistrement est prise en charge et valide. Les devises prises en charge sont dérivées des normes de devise ISO.</td>
    </tr>
    <tr>
      <td>MISSING_BIZIBLE_CUSTOM_FIELDS_PERMISSIONS</td>
      <td>Une erreur s’est produite lors de l’exportation CRM : MISSING_BIZIBLE_CUSTOM_FIELDS_PERMISSIONS : type d’entité « Campagne » : code d’erreur CRM : INVALID_FIELD_FOR_INSERT_UPDATE, champ(s) : bizible2__UniqueId__c, message d’erreur CRM : impossible de créer/mettre à jour les champs : bizible2__UniqueId__c. Vérifiez les paramètres de sécurité de ce champ et qu'il est en lecture/écriture pour votre profil ou votre jeu d'autorisations.</td>
      <td>Il manque des autorisations dans Marketo Measure pour les champs bizible.</td>
      <td>Nous avons besoin d’autorisations en lecture et écriture sur tous les champs précédés du préfixe « bizible2__ ». Une liste complète de ces champs se trouve <a href="/help/configuration-and-setup/marketo-measure-and-salesforce/how-marketo-measure-and-salesforce-interact.md">dans cet article</a>.</td>
    </tr>
    <tr>
      <td>MISSING_CONVERTED_LEAD_PERMISSION</td>
      <td>Une erreur s’est produite lors de l’export CRM : MISSING_CONVERTED_LEAD_PERMISSION.</td>
      <td>Marketo Measure ne dispose pas de l’autorisation Afficher/Modifier les prospects convertis.</td>
      <td>Consultez le document Experience League suivant pour obtenir de l’aide sur l’activation de cette autorisation dans votre CRM.<br/>
          <a href="/help/marketo-measure-salesforce-reporting/additional-functionality/enabling-the-permission-to-edit-converted-leads.md">Activation de l’autorisation pour modifier les prospects convertis</a></td>
    </tr>
    <tr>
      <td>MISSING_FIELD_READ_PERMISSION</td>
      <td>Une erreur s’est produite lors de l’import CRM : MISSING_FIELD_READ_PERMISSION. Type d’entité « Evénement » : INVALID_FIELD:<br/>
    SystemModstamp,IsDeleted,WhoId,bizible2__Bizible_Touchpoint_Date__c</td>
      <td>Marketo Measure ne dispose pas des autorisations de lecture pour un champ obligatoire.</td>
      <td>Reportez-vous aux articles d’aide suivants pour plus d’informations sur les autorisations requises par Marketo Measure :
        <ul>
          <li><a href="/help/marketo-measure-and-dynamics/getting-started-with-marketo-measure-and-dynamics/marketo-measure-dynamics-schema.md">Dynamics</a>
          </li>
          <li><a href="/help/configuration-and-setup/marketo-measure-and-salesforce/how-marketo-measure-and-salesforce-interact.md">Salesforce</a>
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>MISSING_ISREPLICATEABLE_PERMISSION</td>
      <td>Une erreur s’est produite lors de l’import CRM : MISSING_ISREPLICATEABLE_PERMISSION. L’autorisation IsReplicable est manquante dans la campagne.</td>
      <td>Cette autorisation est requise sur les objets Salesforce pour que nous puissions maintenir la synchronisation entre Marketo Measure et Salesforce.</td>
      <td>Contactez l’assistance Salesforce pour obtenir de l’aide sur l’autorisation de réplication des objets.</td>
    </tr>
    <tr>
      <td>MISSING_OBJECT_READ_PERMISSION</td>
      <td>Une erreur s’est produite lors de l’import CRM : MISSING_OBJECT_READ_PERMISSION. Type d’entité « Campagne » : Code d’erreur CRM : MISSING_PERMISSION.</td>
      <td>Marketo Measure ne dispose pas d’autorisations de lecture pour un objet requis.</td>
      <td rowspan="2">Reportez-vous aux articles d’aide suivants pour plus d’informations sur les autorisations requises par Marketo Measure :
          <ul>
            <li><a href="/help/marketo-measure-and-dynamics/getting-started-with-marketo-measure-and-dynamics/marketo-measure-dynamics-schema.md">Dynamics</a>
            </li>
            <li><a href="/help/configuration-and-setup/marketo-measure-and-salesforce/how-marketo-measure-and-salesforce-interact.md">Salesforce</a>
            </li>
          </ul>
      </td>
    </tr>
    <tr>
      <td>MISSING_OBJECT_WRITE_PERMISSION</td>
      <td>Une erreur s’est produite lors de l’export CRM : MISSING_OBJECT_WRITE_PERMISSION. Type d’entité « bizible2_Bizible_Attribution_Touchpoint » : Code d’erreur CRM : MISSING_PERMISSION.</td>
      <td>Marketo Measure ne dispose pas des autorisations d’écriture sur un objet requis.</td>
    </tr>
    <tr>
      <td>MISSING_RECORD_OBJECT_PERMISSIONS</td>
      <td>Une erreur s'est produite lors de l'exportation CRM : MISSING_RECORD_OBJECT_PERMISSIONS : Type d'entité 'bizible2__Bizible_Touchpoint__c' : Code d'erreur CRM : INSUFFISANT_ACCESS_ON_CROSS_REFERENCE_ENTITY, Champ(s) : Compte, Message d'erreur CRM : droits d'accès insuffisants sur l'ID de référence croisée : 0123456</td>
      <td>Autorisations manquantes dans Marketo Measure.</td>
      <td>Plusieurs raisons spécifiques à l’organisation Salesforce sont à l’origine de cette erreur. Vous trouverez ci-dessous quelques étapes de dépannage courantes qui peuvent résoudre le problème :
        <ul>
          <li>Passez en revue toutes les autorisations requises pour chaque <a href="/help/configuration-and-setup/marketo-measure-and-salesforce/how-marketo-measure-and-salesforce-interact.md">objet et champ</a>.</li>
          <li>Excluez l’utilisateur dédié à Marketo Measure des <a href="https://trailhead.salesforce.com/content/learn/modules/validation-rules/bypass-your-validation-rules"> règles de validation personnalisées </a>.</li>
          <li>Octroyez les autorisations « <a href="https://developer.salesforce.com/docs/atlas.en-us.securityImplGuide.meta/securityImplGuide/users_profiles_view_all_mod_all.htm"> Tout modifier </a> Marketo Measure.</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>NULL_EMPTY_CURRENCY_ISO_CODE</td>
      <td>
        <p>
          Une erreur s’est produite lors de l’import CRM : NULL_EMPTY_CURRENCY_ISO_CODE. Le code ISO de devise est NULL ou vide lorsque MultiCurrency est activé pour RecordId 1234.
      </td>
      <td>La devise doit être un code de devise ISO pris en charge.</td>
      <td>Dans le système source indiqué dans la notification (Ad, Crm, Marketo), la devise associée à l’enregistrement est prise en charge et valide. Les devises prises en charge sont dérivées des normes de devise ISO.</td>
    </tr>
    <tr>
      <td>OPERATION_TOO_LARGE</td>
      <td>Une erreur s’est produite lors de l’import CRM : OPERATION_TOO_LARGE. Nous avons besoin de l’autorisation « Afficher toutes les données » pour interroger les activités avec succès.</td>
      <td>Les paramètres de CRM ne permettent pas à Marketo Measure d’interroger un ensemble de données suffisamment volumineux.</td>
      <td>Accordez des autorisations « Afficher toutes les données » à Marketo Measure sur l’objet désigné.
      <p>
      Vous trouverez plus d’informations sur l’autorisation « Afficher toutes les données » <a href="https://developer.salesforce.com/docs/atlas.en-us.securityImplGuide.meta/securityImplGuide/users_profiles_view_all_mod_all.htm">ici</a>.</td>
    </tr>
    <tr>
      <td>RECORD_NONCOMPLIANT_WITH_VALIDATION_RULES</td>
      <td>Une erreur s’est produite lors de l’exportation CRM : RECORD_NONCOMPLIANT_WITH_VALIDATION_RULES : type d’entité « Lead » : Code d’erreur CRM : FIELD_CUSTOM_VALIDATION_EXCEPTION, Champ(s) : Lead_Status_Reason__c, Message d’erreur CRM : vous devez sélectionner le motif du statut du lead, ID d’enregistrement : 0123456</td>
      <td>L’enregistrement en cours de mise à jour ne répond pas à une règle de validation définie dans l’organisation Salesforce.</td>
      <td>Excluez l’utilisateur dédié à Marketo Measure des <a href="https://trailhead.salesforce.com/content/learn/modules/validation-rules/bypass-your-validation-rules"> règles de validation personnalisées </a>.
      <p>
      Mettez à jour vos <a href="https://help.salesforce.com/s/articleView?id=sf.fields_about_field_validation.htm&type=5"> règles de validation </a>.</td>
    </tr>
    <tr>
      <td>RESTRICT_PICKLIST_VALUES_ENABLED</td>
      <td>Une erreur s'est produite lors de l'exportation CRM : RESTRICT_PICKLIST_VALUES_ENABLED : Type d'entité 'Campaign' : Code d'erreur CRM : INVALID_OR_NULL_FOR_RESTRICTED_PICKLIST, Champ(s) : Areas_of_Interest__c, Message d'erreur CRM : valeur incorrecte pour le champ de liste de sélection restreinte : Inconnu</td>
      <td>Lorsque l’option « Restreindre la liste de sélection aux valeurs définies dans le jeu de valeurs » est activée dans la configuration du champ de liste de sélection ou que la valeur insérée dans le champ n’est pas disponible dans le type d’enregistrement de l’objet.</td>
      <td>Désactivez le paramètre Restreindre la liste de sélection dans l’organisation Salesforce.
          <p>
          Excluez l’utilisateur dédié à Marketo Measure des <a href="https://trailhead.salesforce.com/content/learn/modules/validation-rules/bypass-your-validation-rules"> règles de validation personnalisées </a>.
      </td>
    </tr>
    <tr>
      <td>REQUIRED_FIELD_MISSING</td>
      <td>Une erreur s'est produite lors de l'exportation CRM : MISSING_REQUIRED_FIELD : Type d'entité 'Lead' : Code d'erreur CRM : REQUIRED_FIELD_MISSING, Champ(s) : Product_Type__c, Message d'erreur CRM : champs obligatoires manquants : [Product_Type__c], ID d'enregistrement : 0123456</td>
      <td>Lorsqu’une règle de validation spécifie des champs obligatoires sur des objets.</td>
      <td>Excluez l’utilisateur dédié à Marketo Measure des <a href="https://trailhead.salesforce.com/content/learn/modules/validation-rules/bypass-your-validation-rules"> règles de validation personnalisées </a>.
      </td>
    </tr>
    <tr>
      <td>UNKNOWN_EXCEPTION</td>
      <td>Une erreur s'est produite lors de l'exportation CRM : UNKNOWN_EXCEPTION : Type d'entité 'Contact' : Code d'erreur CRM : UNKNOWN_EXCEPTION, Message d'erreur CRM : les utilisateurs du portail ne peuvent pas posséder de comptes partenaires, ID d'enregistrement : 0123456</td>
      <td>Une exception non gérée s’est produite dans Salesforce.</td>
      <td>Si le problème persiste, signalez-le à Salesforce et copiez les valeurs numériques dans le message d’erreur.</td>
    </tr>
    <tr>
      <td>UNSUPPORTED_CRM_PACKAGE_VERSION</td>
      <td>Une erreur s’est produite lors de l’importation crm : UNSUPPORTED_CRM_PACKAGE_VERSION : mettez à jour votre package crm</td>
      <td>Le package détecté n’est plus pris en charge.</td>
      <td>Mettez à niveau votre package vers la version la plus récente :
        <ul>
          <li><a href="/help/configuration-and-setup/marketo-measure-and-salesforce/best-practices-for-marketo-measure-crm-package.md">Bonnes pratiques</a>
          </li>
          <li><a href="/help/marketo-measure-and-dynamics/getting-started-with-marketo-measure-and-dynamics/microsoft-dynamics-crm-installation-guide.md">Dynamics</a>
          </li>
          <li><a href="/help/configuration-and-setup/marketo-measure-and-salesforce/marketo-measure-salesforce-package-installation-and-set-up.md">Salesforce</a>
          </li>
        </ul>
      </td>
    </tr>
  </tbody>
</table>
