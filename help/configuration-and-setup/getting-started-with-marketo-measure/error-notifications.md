---
description: Notifications d’erreur - [!DNL Marketo Measure]
title: Notifications d’erreur
feature: Fundamentals
source-git-commit: 915e9c5a968ffd9de713b4308cadb91768613fc5
workflow-type: tm+mt
source-wordcount: '607'
ht-degree: 95%

---

# Notifications d’erreur {#error-notifications}

Vous trouverez ci-dessous une liste des erreurs que vous pouvez recevoir par notification dans l’application ou par e-mail. Si vous recevez l’une de ces notifications, suivez les étapes de dépannage correspondantes. Si ces étapes ne résolvent pas le problème, contactez le [Support de Marketo](https://nation.marketo.com/t5/support/ct-p/Support).

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
      <td>Reportez-vous à la documentation Salesforce suivante pour savoir <a href="https://help.salesforce.com/s/articleView?id=sf.branded_apps_commun_api_permset.htm&amp;type=5">comment activer l’accès aux API</a>.</td>
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
           <img src="assets/error-notifications-1.png">
          </p>
      </td>
    </tr>
    <tr>
      <td>INVALID_ADOBE_ANALYTICS_CONFIGURATION</td>
      <td>Une erreur s’est produite lors de l’export d’Adobe Analytics : INVALID_ADOBE_ANALYTICS_CONFIGURATION. Erreur : chargement non autorisé. Confirmez le schéma de la source de données avant de le charger. ID de la source de données : 1234</td>
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
      <td>Dans le système source indiqué dans la notification (annonce publicitaire, CRM, Marketo), vérifiez que la devise associée à l’enregistrement comporte une devise prise en charge et valide. Les devises prises en charge sont dérivées des normes de devise ISO.</td>
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
      <td>NULL_EMPTY_CURRENCY_ISO_CODE</td>
      <td>
        <p>
          Une erreur s’est produite lors de l’import CRM : NULL_EMPTY_CURRENCY_ISO_CODE. Le code ISO de devise est NULL ou vide lorsque MultiCurrency est activé pour RecordId 1234.
      </td>
      <td>La devise doit être un code de devise ISO pris en charge.</td>
      <td>Dans le système source indiqué dans la notification (annonce publicitaire, CRM, Marketo), vérifiez que la devise associée à l’enregistrement comporte une devise prise en charge et valide. Les devises prises en charge sont dérivées des normes de devise ISO.</td>
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
