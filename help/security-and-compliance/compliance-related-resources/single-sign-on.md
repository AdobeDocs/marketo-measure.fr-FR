---
unique-page-id: 18874761
description: Authentification unique - [!DNL Marketo Measure]
title: Authentification unique SSO
exl-id: a328e9cb-8352-4693-8a44-533e08f1a29c
source-git-commit: 4787f765348da71bc149c997470ce678ba498772
workflow-type: tm+mt
source-wordcount: '1276'
ht-degree: 0%

---

# Authentification unique SSO {#single-sign-on}

Le langage SAML (langage de balisage d’assertion de sécurité) pour SSO (authentification unique) permet aux utilisateurs de s’authentifier par le biais du fournisseur d’identité d’une entreprise lorsqu’ils se connectent au [!DNL Marketo Measure] application. La connexion unique permet à un utilisateur de s’authentifier une seule fois, sans avoir à authentifier des applications distinctes. SAML est une nécessité pour les clients d’entreprise, car tous les utilisateurs n’ont pas une [!DNL Salesforce] ou [!DNL Google] au sein de leur organisation. Pour mettre à l’échelle, [!DNL Marketo Measure] a développé une solution SAML qui peut prendre en charge les fournisseurs d’identité de l’entreprise.

>[!CAUTION]
>
>Cet article décrit l’authentification unique (SSO) et la gestion avancée des utilisateurs CRM. Si votre compte a été configuré **after 9/10/2020**, ignorez cet article, car SSO et Identity Management seront configurés dans la variable [Adobe Admin Console pour votre [!DNL Marketo Measure] integration](/help/configuration-and-setup/getting-started-with-marketo-measure/marketo-measure-quick-start.md).

>[!NOTE]
>
>Il est probable que les entreprises utilisent différents fournisseurs d’identité (par exemple, Ping Identity, Okta). Les termes utilisés dans les instructions de configuration suivantes et dans l’interface utilisateur peuvent ne pas correspondre directement à ceux utilisés par votre fournisseur d’identité.

## Exigences {#requirements}

* Utilisateur avec les autorisations AccountAdmin dans [!DNL Marketo Measure] Application
* Utilisateur disposant d’un accès administratif au fournisseur d’identité du client

## Prise en main {#getting-started}

Pour commencer, accédez à la page Paramètres > Sécurité > Authentification dans le [!DNL Marketo Measure] application. Puis, basculez le type de connexion sur SSO personnalisé pour afficher les options de configuration. Les modifications ne prennent effet que lorsque vous testez votre authentification et cliquez sur le bouton **[!UICONTROL Enregistrer]** en bas de la page.

![](assets/single-sign-on-1.png)

## Processus {#process}

[!DNL Marketo Measure] L’authentification unique requiert la configuration de vos paramètres d’authentification en une série d’étapes afin que vous ne risquiez pas d’être verrouillé hors de votre [!DNL Marketo Measure] compte .

Configurez la variable [!DNL Marketo Measure] Application dans votre fournisseur d’identité. Consultez la documentation externe répertoriée ci-dessous pour obtenir des instructions pas à pas.

    a. Lorsque vous êtes invité à saisir l’URL de connexion unique, l’URL du destinataire ou l’URL de destination, l’URL du service client d’assertion SAML (ACS), utilisez [https://apps.bizible.com/BizibleSAML2/ReceiveSSORequest](https://apps.bizible.com/BizibleSAML2/ReceiveSSORequest)
    
    b. Lorsque vous êtes invité à saisir l’URL de restriction d’audience ou l’identifiant unique défini par l’application, utilisez [https://BizibleLPM](https://biziblelpm/)

Basculez vers SSO personnalisé dans la [!DNL Marketo Measure] Application

    a. Une fois que le groupe de facturation a été activé pour votre compte, vous pouvez accéder à [!UICONTROL Paramètres] &quot;[!UICONTROL Sécurité] &quot; [!UICONTROL Authentification]
    
    b. Par défaut, votre Type de connexion est défini sur &quot;Utilisateurs CRM&quot;.
    
    c. Basculez le type de connexion sur &quot;SSO personnalisé&quot; pour lancer le processus de configuration.

Renseignez les paramètres de connexion pour votre configuration du fournisseur d’identité.

    a. Votre fournisseur d’identité peut fournir un document de métadonnées IdP .xml qui extrait les champs de configuration requis. Chargez le contenu du document .xml ou remplissez les trois champs ci-dessous à partir de la sortie obtenue lors du processus de configuration du fournisseur d’identités. **Vous n’avez pas besoin d’effectuer les deux.**
    
    i. URL IdP : URL qui [!DNL Marketo Measure] doit pointer vers pour authentifier vos utilisateurs dans la variable [!DNL Marketo Measure] application. Parfois appelée &quot;URL de redirection&quot;.
    ii. IdP Issuer : identifiant unique du fournisseur d’identité. Parfois appelée &quot;clé externe&quot;.
    iii. Certificat IdP : clé publique qui permet [!DNL Marketo Measure] pour vérifier et valider la signature de toutes les réponses du fournisseur d’identité.

Définissez l’expiration du jeton pour vos utilisateurs en minutes.

    a. [!DNL Marketo Measure] permet un nombre entier compris entre 1 et 1 440 minutes. Une fois le délai de session d’un utilisateur dépassé, il est déconnecté lorsqu’il accède à une nouvelle page.

Configurez et mappez vos paramètres Attribut utilisateur avec le prénom, le nom et l’adresse électronique respectifs.

    a. En saisissant les attributs SAML, [!DNL Marketo Measure] pourront reconnaître vos utilisateurs en fonction des informations transmises.
    
    i. Attribut de courriel : indiquez le nom d’attribut utilisé par votre fournisseur d’identité pour l’adresse électronique de l’utilisateur.
    ii. Attribut de prénom : indiquez le nom d’attribut utilisé par votre fournisseur d’identité pour le prénom de l’utilisateur.
    iii. Attribut Nom : indiquez le nom d’attribut utilisé par votre fournisseur d’identité pour le nom de l’utilisateur.
    
    b. Conseil : si vous testez maintenant votre configuration SAML, nous allons analyser les attributs Email, Prénom et Nom que vous pouvez utiliser pour cette section.

![](assets/single-sign-on-2.png)

Configurez et mappez vos paramètres de rôle utilisateur aux rôles ou groupes respectifs classés dans votre IdP.

    a. Les clients ont la possibilité d’affecter des [!DNL Marketo Measure] rôles utilisateur basés sur des groupes définis dans leur fournisseur d’identité. En saisissant vos attributs SAML, [!DNL Marketo Measure] pourra mapper les rôles et les groupes de votre utilisateur à [!DNL Marketo Measure] autorisations utilisateur. Nous vous recommandons vivement de configurer ces rôles afin que votre [!DNL Marketo Measure] L’administrateur dispose des droits suffisants pour mettre à jour votre compte.
    
    b. Si aucun rôle ou groupe n’est mappé, le paramètre par défaut est que tous les employés du fournisseur d’identité auront accès aux utilisateurs standard.
    
    i. [!DNL Marketo Measure] Utilisateur standard : indiquez la valeur de rôle ou de groupe (de votre fournisseur d’authentification unique) pour les utilisateurs qui doivent disposer d’un accès en lecture seule à la variable [!DNL Marketo Measure] application.
    ii. [!DNL Marketo Measure] Utilisateur administrateur du compte : indiquez le rôle ou la valeur de groupe (de votre fournisseur d’authentification unique) pour les utilisateurs qui doivent disposer d’un accès administratif à [!DNL Marketo Measure] application. Cela signifie que le rôle a accès à la modification des configurations et des paramètres liés à votre compte.
    iii. Vous devez avoir un attribut dans votre IdP avec le nom exact des &quot;groupes&quot; qui contient les valeurs que vous avez placées dans les attributs &quot;Utilisateur standard Bizible&quot; ou &quot;Utilisateur administrateur de compte Bizible&quot;.
    
    c. Si plusieurs rôles ou groupes doivent être mappés à un rôle, saisissez chaque valeur séparée par une virgule.

![](assets/single-sign-on-3.png)

Test de la configuration de l’authentification unique

    a. Avant de pouvoir appuyer sur Enregistrer, vous devez cliquer sur le bouton [!UICONTROL Test de l’authentification SAML] pour vérifier que vos paramètres ont été correctement configurés.
    
    b. Si une erreur &quot;échec&quot; s’affiche, suivez le message et réessayez.

![](assets/single-sign-on-4.png)

Enregistrez vos paramètres et demandez à vos collègues d’utiliser [!UICONTROL Authentification unique] avec votre nouvelle URL de connexion personnalisée.

    a. Important : Une fois que vous avez enregistré vos nouveaux paramètres d’authentification, il est possible que votre session se termine une fois que vous accédez à une nouvelle page, car vous avez désactivé la connexion par les utilisateurs CRM et activé l’authentification unique personnalisée.

![](assets/single-sign-on-5.png)

Essaie-le !

    a. Utilisez votre nouvelle URL de connexion personnalisée et tentez de vous reconnecter au [!DNL Marketo Measure] Application avec vos informations d’identification de fournisseur d’identité.
    
    b. Le format ressemblera à &quot;https://apps.adobe.com/business/[nom_compte]&quot;
    
    c. Félicitations ! Vous avez correctement configuré l’authentification unique dans le [!DNL Marketo Measure] Demande pour votre compte !

![](assets/single-sign-on-6.png)

>[!NOTE]
>
>Après avoir configuré l’authentification unique, vous n’aurez plus besoin d’ajouter des utilisateurs dans la variable [!DNL Marketo Measure] application. La mise en service des utilisateurs doit être gérée directement dans votre fournisseur d’identité.

## Utilisateurs de CRM (configuration avancée) {#crm-users-advanced-setup}

Par défaut, tous les comptes peuvent accéder à la variable [!DNL Marketo Measure] à l’aide de leurs informations d’identification CRM. Parfois, les propriétaires de compte doivent limiter l’accès à certains rôles et ne pas l’ouvrir à tous les utilisateurs disposant d’une licence CRM active. La configuration avancée vous permet de mapper vos rôles et groupes CRM à [!DNL Marketo Measure] autorisations utilisateur.

Si aucun rôle ou groupe n’est mappé, le paramètre par défaut est que toutes les licences actives dans votre CRM disposent d’un accès utilisateur standard.

* [!DNL Marketo Measure] Utilisateur standard : indiquez la valeur de rôle ou de groupe pour les utilisateurs qui doivent disposer d’un accès en lecture seule au [!DNL Marketo Measure] application.
* [!DNL Marketo Measure] Utilisateur administrateur du compte : indiquez la valeur de rôle ou de groupe pour les utilisateurs qui doivent disposer d’un accès administratif à la variable [!DNL Marketo Measure] application. Cela signifie que le rôle a accès à la modification des configurations et des paramètres liés à votre compte.

Si plusieurs rôles ou groupes doivent être mappés à un rôle, saisissez chaque valeur séparée par une virgule.

**Rôles Salesforce**

Pour [!DNL Salesforce] Rôles, utilisez le nom de chaque rôle. Tous les rôles se trouvent sous [!UICONTROL Configuration] >[!UICONTROL Gestion des utilisateurs] >[!UICONTROL Rôles] .

![](assets/6.png)

**Rôles Dynamics**

Pour [!DNL Dynamics] Rôles, utilisez le nom de chaque rôle de sécurité. Tous les rôles de sécurité sont disponibles sous [!UICONTROL Paramètres] >[!UICONTROL Sécurité] >[!UICONTROL Rôles de sécurité] .

![](assets/7.png)

![](assets/8.png)

**Utilisateurs de Google**

Une fois l’authentification unique personnalisée configurée, la variable [!UICONTROL Utilisateurs] est mise à jour afin d’afficher uniquement les utilisateurs externes qui ont été ajoutés avec les connexions Google. Comme tous les utilisateurs ayant accès à sont définis par le biais de la configuration SSO, d’autres utilisateurs externes sont répertoriés ici.

![](assets/9.png)

Uniquement valide [!DNL Google] vous pouvez ajouter des comptes et un rôle utilisateur doit être défini.

## Liens externes {#external-links}

* [Okta](https://developer.okta.com/standards/SAML/setting_up_a_saml_application_in_okta)
* [Identité Ping](https://docs.pingidentity.com:443/bundle/p1_enterpriseConfigSsoSaml_cas/page/enableAppWithoutURL.html)
* [OneLogin](https://onelogin.service-now.com/support?id=kb_article&amp;sys_id=b2c91143db109700d5505eea4b9619d5)
* [Active Directory](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-saas-custom-apps)
