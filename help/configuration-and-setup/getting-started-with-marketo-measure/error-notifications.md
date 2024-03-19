---
description: Notifications d’erreur - [!DNL Marketo Measure]
title: Notifications d’erreur
feature: Fundamentals
exl-id: ed07eed6-ddeb-4856-a1ac-ea3d571283f6
source-git-commit: 20f886a0c6f448956ad2fda2d21a25f8d9a5a6af
workflow-type: tm+mt
source-wordcount: '1692'
ht-degree: 30%

---

# Notifications d’erreur {#error-notifications}

Vous trouverez ci-dessous une liste des erreurs que vous pouvez recevoir par notification ou email in-app. Si vous recevez l’une de ces notifications, suivez les étapes de dépannage correspondantes. Si ces étapes ne résolvent pas le problème, contactez le [Support de Marketo](https://nation.marketo.com/t5/support/ct-p/Support).

Pour afficher le message de notification complet dans [!DNL Marketo Measure], cliquez sur **Afficher tout** au bas de l’onglet Notifications.

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
      <td>Reportez-vous à la documentation Salesforce suivante pour savoir <a href="https://help.salesforce.com/s/articleView?language=en_US&amp;id=sf.branded_apps_commun_api_permset.htm&amp;type=5">comment activer l’accès aux API</a>.</td>
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
      <td>Une erreur s’est produite lors de l’exportation Crm : CANNOT_EXECUTE_FLOW_TRIGGER : type d’entité 'Contact' Donnez ces détails à votre administrateur Salesforce.
Limite dépassée Vous ou votre organisation avez dépassé la limite maximale pour cette fonctionnalité. ID d’erreur : 123456</td>
      <td>L’enregistrement ne peut pas être enregistré, car il ne répond pas à une règle de flux de déclenchement configurée dans l’organisation Salesforce.</td>
      <td>Passez en revue les détails complets du message de notification et passez en revue les déclencheurs de flux dans l’organisation Salesforce.
Documentation Salesforce sur les déclencheurs de flux <a href="https://admin.salesforce.com/blog/2023/what-is-a-record-triggered-flow#:~:text=A%20record%2Dtriggered%20flow%20allows,is%20created%20and%2For%20updated">peut être consulté ici</a>.
      </td>
    </tr>
    <tr>
      <td>CANNOT_INSERT_UPDATE_ACTIVATE_ENTITY</td>
      <td>Une erreur s’est produite lors de l’export Crm : CANNOT_INSERT_UPDATE_ACTIVATE_ENTITY : Type d’entité 'Lead' : Code d’erreur CRM : CANNOT_INSERT_UPDATE_ACTIVATE_ENTITY, Message d’erreur CRM : System.LimitException : dépassement de la limite de temps du processeur Apex, RecordId : 0123456
      <p>
      Une erreur s’est produite lors de l’export Crm : CANNOT_INSERT_UPDATE_ACTIVATE_ENTITY : Type d’entité 'Account' : Code d’erreur CRM : CANNOT_INSERT_UPDATE_ACTIVATE_ENTITY, Message d’erreur CRM : le type d’entité ne peut pas être mis à jour : Account, RecordId : 0123456</td>
      <td>Les déclencheurs empêchent la mise à jour ou l’insertion d’un objet.
      <p>
      OR
      <p>
      Autorisations manquantes sur l’objet.</td>
      <td>Vérifiez le code de déclenchement, ce qui entraîne l’échec de l’insertion/de la mise à jour. Pour plus d’informations sur les déclencheurs, consultez la documentation Salesforce suivante :
        <ul>
          <li><a href="https://help.salesforce.com/s/articleView?id=sf.code_manage_triggers.htm&amp;type=5">Triggers Apex</a>
          </li>
          <li><a href="https://admin.salesforce.com/blog/2023/what-is-a-record-triggered-flow#:~:text=A%20record%2Dtriggered%20flow%20allows,is%20created%20and%2For%20updated">Déclencheurs de flux</a>
          </li>
        </ul>
        <p>
        Fournissez toutes les autorisations nécessaires au <a href="/help/configuration-and-setup/marketo-measure-and-salesforce/how-marketo-measure-and-salesforce-interact.md">Utilisateur Marketo Measure</a>.
      </td>
    </tr>
    <tr>
      <td>DUPLICATES_DETECTED</td>
      <td>Une erreur s'est produite lors de l'export Crm : DUPLICATES_DETECTED : Type d'entité 'Contact' : Code d'erreur CRM : DUPLICATES_DETECTED, Message d'erreur CRM : vous créez un enregistrement en double. Nous vous recommandons plutôt d'utiliser un enregistrement existant., RecordId: 0123456</td>
      <td>L’enregistrement en cours d’importation dans l’organisation Salesforce existe déjà.</td>
      <td><a href="https://help.salesforce.com/s/articleView?id=000390009&amp;type=1">Désactivation du paramètre "Dupliquer la règle"</a> pour permettre les doublons.
          <p>
          Exclure l’utilisateur dédié Marketo Measure de <a href="https://trailhead.salesforce.com/content/learn/modules/validation-rules/bypass-your-validation-rules">règles de validation personnalisées</a>.</td>
    </tr>
    <tr>
      <td>DUPLICATE_VALUE</td>
      <td>Une erreur s’est produite lors de l’export Crm : DUPLICATE_VALUE : Type d’entité 'Lead' : Code d’erreur CRM : DUPLICATE_VALUE, Message d’erreur CRM : valeur en double trouvée : Email_Unique__c duplique la valeur de l’enregistrement avec l’ID : 123, RecordId : 456</td>
      <td>Le champ importé dans l’organisation Salesforce n’autorise pas les valeurs en double.</td>
      <td>Décochez la case <a href="https://help.salesforce.com/s/articleView?id=000390009&amp;type=1">"Case à cocher unique"</a> dans Salesforce.
          <p>
          Exclure l’utilisateur dédié Marketo Measure de <a href="https://trailhead.salesforce.com/content/learn/modules/validation-rules/bypass-your-validation-rules">règles de validation personnalisées</a>.</td>
    </tr>
    <tr>
      <td>ENTITY_IS_LOCKED</td>
      <td>Une erreur s’est produite lors de l’export Crm : ENTITY_IS_LOCKED : Type d’entité 'Compte' : Code d’erreur CRM : ENTITY_IS_LOCKED, Message d’erreur CRM : cet enregistrement est verrouillé. Si vous devez le modifier, contactez votre administrateur., RecordId : 0123456</td>
      <td>Lorsqu’un enregistrement se trouve dans un processus d’approbation et qu’un utilisateur qui n’est pas l’approbateur ou l’administrateur système actuel tente de modifier l’enregistrement.</td>
      <td>
        <ul>
          <li>Résolvez le processus d’approbation en attente pour cet enregistrement dans l’organisation Salesforce.</li>
          <li>Exclure l’utilisateur dédié Marketo Measure de <a href="https://trailhead.salesforce.com/content/learn/modules/validation-rules/bypass-your-validation-rules">règles de validation personnalisées</a>.
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>FIELD_FILTER_VALIDATION_EXCEPTION</td>
      <td>Une erreur s’est produite lors de l’export Crm : FIELD_FILTER_VALIDATION_EXCEPTION : Type d’entité 'Lead' : Code d’erreur CRM : FIELD_FILTER_VALIDATION_EXCEPTION, Champ(s) : User__C, Message d’erreur CRM : la valeur n’existe pas ou ne correspond pas aux critères de filtrage. Sélectionnez un utilisateur avec le rôle "Responsable de compte, Ventes internes" ; IdEnregistrement : 0123456</td>
      <td>L’enregistrement modifié ne satisfait plus les filtres de recherche définis sur l’objet.</td>
      <td>Recherchez des filtres sur l’objet que Marketo Measure tente de modifier. Voir <a href="https://help.salesforce.com/s/articleView?id=000384756&amp;type=1">cet article de Salesforce</a> pour savoir comment vérifier les filtres sur un objet.</td>
    </tr>
    <tr>
      <td>FIELD_INTEGRITY_EXCEPTION</td>
      <td>Une erreur s’est produite lors de l’export Crm : FIELD_INTEGRITY_EXCEPTION : Type d’entité 'Lead' : Code d’erreur CRM : FIELD_INTEGRITY_EXCEPTION, Champ(s) : Pays, Message d’erreur CRM : un problème est survenu dans ce pays, même s’il semble correct. Sélectionnez un pays/un territoire dans la liste des pays valides.: Pays, RecordId : 0123456</td>
      <td>Le type attendu de l’enregistrement ne correspond pas.</td>
      <td>Le cas le plus courant est de ne pas respecter les normes de nommage Etat/Pays définies dans l’organisation Salesforce, car les champs Etat/Pays ont été normalisés pour n’accepter que certaines valeurs de liste de sélection. Pour résoudre ce problème, vous pouvez :
        <ul>
          <li>Mettez à jour l’enregistrement pour suivre les valeurs acceptées par l’organisation pour ce champ. Contactez votre administrateur SFDC pour obtenir la liste des valeurs acceptées.</li>
          <li><a href="https://help.salesforce.com/s/articleView?id=sf.admin_state_country_picklist_enable.htm&amp;type=5">Désactiver les listes de sélection Etat/Pays</a>.
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>INACTIVE_OWNER_OR_USER</td>
      <td>Une erreur s'est produite lors de l'export Crm : INACTIVE_OWNER_OR_USER : Type d'entité 'Contact' : Code d'erreur CRM : INACTIVE_OWNER_OR_USER, Message d'erreur CRM : opération effectuée avec l'utilisateur inactif [1234] en tant que propriétaire du contact, RecordId : 0123456</td>
      <td>Marketo Measure ne dispose pas de l’autorisation "Mettre à jour les enregistrements avec les propriétaires inactifs".</td>
      <td>Accorder à Marketo Measure le<a href="https://help.salesforce.com/s/articleView?id=000386699&amp;type=1">Mise à jour d’enregistrements avec des propriétaires inactifs</a>".</td>
    </tr>
    <tr>
      <td>INSUFFICIENT_ACCESS_OR_READONLY</td>
      <td>Une erreur s’est produite lors de l’export Crm : INSUFFICIENT_ACCESS_OR_READONLY : type d’entité 'Compte' : Code d’erreur CRM : INSUFFICIENT_ACCESS_OR_READONLY, Message d’erreur CRM : droits d’accès insuffisants sur l’ID d’objet : [123], RecordId : 456</td>
      <td>Marketo Measure ne dispose pas d’autorisations sur un objet/champ ou l’objet est en lecture seule.</td>
      <td>Reportez-vous aux <a href="/help/configuration-and-setup/marketo-measure-and-salesforce/how-marketo-measure-and-salesforce-interact.md">Article Experience League</a> pour plus d’informations sur les autorisations requises par Marketo Measure.</td>
    </tr>
    <tr>
      <td>INVALID_ADOBE_ANALYTICS_CONFIGURATION</td>
      <td>Une erreur s’est produite pendant l’exportation Adobe Analytics : INVALID_ADOBE_ANALYTICS_CONFIGURATION : Erreur : Téléchargement non autorisé. Confirmez le schéma de la source de données avant de le charger. ID de la source de données : 1234</td>
      <td>L’intégration d’Adobe Analytics n’est pas configurée correctement.</td>
      <td>Pour garantir une configuration correcte, reportez-vous aux articles d’aide suivants :
        <ul>
          <li>
            <a href="/help/marketo-measure-and-adobe/marketo-measure-integrations-with-adobe-analytics.md">Intégrations de Marketo Measure à Adobe Analytics</a>
          </li>
          <li>
            <a href="https://experienceleague.adobe.com/docs/core-services/interface/services/customer-attributes/t-crs-usecase.html">Création d’une source d’attributs du client et chargement du fichier de données</a>
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
      <td>Dans le système source indiqué dans la notification (Ad, Crm, Marketo), assurez-vous que la devise associée à l’enregistrement dispose d’une devise prise en charge et valide. Les devises prises en charge sont dérivées des normes de devise ISO.</td>
    </tr>
    <tr>
      <td>MISSING_BIZIBLE_CUSTOM_FIELDS_PERMISSIONS</td>
      <td>Une erreur s’est produite lors de l’export Crm : MISSING_BIZIBLE_CUSTOM_FIELDS_PERMISSIONS : Type d’entité 'Campaign' : Code d’erreur CRM : INVALID_FIELD_FOR_INSERT_UPDATE, Champ(s) : bizible2__UniqueId__c, Message d’erreur CRM : impossible de créer/mettre à jour les champs : bizible2__queId__c. Vérifiez les paramètres de sécurité de ce champ et vérifiez qu’il est en lecture/écriture pour votre profil ou jeu d’autorisations.</td>
      <td>Marketo Measure ne dispose pas d’autorisations sur les champs de bizible.</td>
      <td>Nous avons besoin d’autorisations de lecture et d’écriture sur tous les champs dont le préfixe est "bizible2__". Une liste complète de ces champs est disponible <a href="/help/configuration-and-setup/marketo-measure-and-salesforce/how-marketo-measure-and-salesforce-interact.md">dans cet article</a>.</td>
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
      <td>Une erreur s’est produite lors de l’export Crm : MISSING_RECORD_OBJECT_PERMISSIONS : type d’entité 'bizible2__Bizible_Touchpoint__c' : Code d’erreur CRM : INSUFFICIENT_ACCESS_ON_CROSS_REFERENCE_ENTITY, champ(s) : Compte, CRM ErrorMessage : droits d’accès insuffisants sur l’ID de référence croisée : 0123456</td>
      <td>Marketo Measure ne dispose pas d’autorisations.</td>
      <td>Plusieurs raisons expliquent cette erreur et sont spécifiques à l’organisation Salesforce. Vous trouverez ci-dessous quelques étapes courantes de dépannage qui peuvent résoudre le problème :
        <ul>
          <li>Examinez toutes les autorisations dont nous avons besoin pour chaque <a href="/help/configuration-and-setup/marketo-measure-and-salesforce/how-marketo-measure-and-salesforce-interact.md">objet et champ</a>.</li>
          <li>Exclure l’utilisateur dédié Marketo Measure de <a href="https://trailhead.salesforce.com/content/learn/modules/validation-rules/bypass-your-validation-rules">règles de validation personnalisées</a>.</li>
          <li>Accorder Marketo Measure "<a href="https://developer.salesforce.com/docs/atlas.en-us.securityImplGuide.meta/securityImplGuide/users_profiles_view_all_mod_all.htm">Modifier tout</a>".</li>
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
      <td>Dans le système source indiqué dans la notification (Ad, Crm, Marketo), assurez-vous que la devise associée à l’enregistrement dispose d’une devise prise en charge et valide. Les devises prises en charge sont dérivées des normes de devise ISO.</td>
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
      <td>Une erreur s’est produite lors de l’exportation Crm : RECORD_NONCOMPLIANT_WITH_VALIDATION_RULES : Type d’entité 'Lead' : Code d’erreur CRM : FIELD_CUSTOM_VALIDATION_EXCEPTION, Champ(s) : Lead_Status_Reason__c, Message d’erreur CRM : vous devez sélectionner le motif de l’état de piste, RecordId : 0123456</td>
      <td>L’enregistrement mis à jour ne respecte pas une règle de validation définie dans l’organisation Salesforce.</td>
      <td>Exclure l’utilisateur dédié Marketo Measure de <a href="https://trailhead.salesforce.com/content/learn/modules/validation-rules/bypass-your-validation-rules">règles de validation personnalisées</a>.
      <p>
      Mettez à jour votre <a href="https://help.salesforce.com/s/articleView?id=sf.fields_about_field_validation.htm&amp;type=5">règles de validation</a>.</td>
    </tr>
    <tr>
      <td>RESTRICT_PICKLIST_VALUES_ENABLED</td>
      <td>Une erreur s’est produite lors de l’exportation Crm : RESTRICT_PICKLIST_VALUES_ENABLED : type d’entité 'Campaign' : Code d’erreur CRM : INVALID_OR_NULL_FOR_RESTRICTED_PICKLIST, champ(s) : Zones_of_Interest__c, Message d’erreur CRM : mauvaise valeur pour le champ de liste de sélection restreint : Inconnu</td>
      <td>Lorsque "Restreindre la liste de sélection aux valeurs définies dans l’ensemble de valeurs" est activé dans la configuration du champ de liste de sélection ou que la valeur insérée dans le champ n’est pas disponible dans le type d’enregistrement de l’objet.</td>
      <td>Désactivez le paramètre Restreindre la liste de sélection dans l’organisation Salesforce.
          <p>
          Exclure l’utilisateur dédié Marketo Measure de <a href="https://trailhead.salesforce.com/content/learn/modules/validation-rules/bypass-your-validation-rules">règles de validation personnalisées</a>.
      </td>
    </tr>
    <tr>
      <td>REQUIRED_FIELD_MISSING</td>
      <td>Une erreur s’est produite lors de l’exportation Crm : MISSING_REQUIRED_FIELD : Type d’entité 'Lead' : Code d’erreur CRM : REQUIRED_FIELD_MISSING, Champ(s) : Product_Type__c, Message d’erreur CRM : les champs obligatoires sont manquants : [Product_Type__c], RecordId : 0123456</td>
      <td>Lorsqu’une règle de validation spécifie les champs obligatoires sur les objets.</td>
      <td>Exclure l’utilisateur dédié Marketo Measure de <a href="https://trailhead.salesforce.com/content/learn/modules/validation-rules/bypass-your-validation-rules">règles de validation personnalisées</a>.
      </td>
    </tr>
    <tr>
      <td>UNKNOWN_EXCEPTION</td>
      <td>Une erreur s'est produite lors de l'export Crm : UNKNOWN_EXCEPTION : Type d'entité 'Contact' : Code d'erreur CRM : UNKNOWN_EXCEPTION, Message d'erreur CRM : les utilisateurs du portail ne peuvent pas posséder de comptes de partenaire, RecordId : 0123456</td>
      <td>Une exception non gérée s’est produite dans Salesforce.</td>
      <td>Si le problème persiste, enregistrez une casse avec Salesforce et copiez les valeurs numériques dans le message d’erreur.</td>
    </tr>
    <tr>
      <td>UNSUPPORTED_CRM_PACKAGE_VERSION</td>
      <td>Une erreur s’est produite lors de l’importation Crm : UNSUPPORTED_CRM_PACKAGE_VERSION : mettez à jour votre package crm</td>
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
