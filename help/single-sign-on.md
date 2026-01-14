---
description: Conseils sur l’authentification unique pour les utilisateurs de Marketo Measure
title: Authentification unique SSO
exl-id: a328e9cb-8352-4693-8a44-533e08f1a29c
source-git-commit: fcd8e276c85669ddf12bd7404fb12d3e99b2642a
workflow-type: tm+mt
source-wordcount: '1395'
ht-degree: 91%

---

# Authentification unique SSO {#single-sign-on}

SAML (Security Assertion Markup Language) pour SSO (Single Sign-On, authentification unique) permet aux utilisateurs et utilisatrices de s’authentifier par le biais du fournisseur d’identité de l’entreprise lorsqu’ils se connectent à l’application [!DNL Marketo Measure]. La SSO permet à un utilisateur ou une utilisatrice de s’authentifier une seule fois, sans avoir besoin d’authentifier des applications distinctes. SAML est une nécessité pour la clientèle d’entreprise, car tous les utilisateurs et utilisatrices ne disposent pas d’un compte [!DNL Salesforce] ou [!DNL Google] au sein de leur organisation. Pour s’adapter, [!DNL Marketo Measure] a développé une solution SAML qui peut prendre en charge les fournisseurs d’identité de l’entreprise.

>[!CAUTION]
>
>Cet article présente l’authentification unique (SSO) et la gestion de la relation client (CRM) avancée User Management. Si votre compte a été créé **après le 10/09/2020**, ne tenez pas compte de cet article, car la SSO et Identity Management seront configurés dans [Adobe Admin Console de votre intégration [!DNL Marketo Measure] ](/help/implementation-guide.md).

>[!NOTE]
>
>Il est probable que les entreprises utilisent différents fournisseurs d’identité (par exemple, Ping Identity, Okta). Les termes utilisés dans les instructions de configuration suivantes et dans l’interface utilisateur peuvent ne pas correspondre exactement à ceux utilisés par votre fournisseur d’identité.

## Exigences {#requirements}

* Utilisateur ou utilisatrice disposant des autorisations AccountAdmin dans l’application [!DNL Marketo Measure]
* Utilisateur ou utilisatrice disposant d’un accès administratif au fournisseur d’identité du client ou de la cliente

## Prise en main {#getting-started}

Pour commencer, accédez à la page Paramètres > Sécurité > Authentification dans l’application [!DNL Marketo Measure]. Définissez ensuite le type de connexion sur SSO personnalisée pour voir les options de configuration. Les modifications ne prendront effet que lorsque vous aurez testé votre authentification et cliqué sur le bouton **[!UICONTROL Enregistrer]** au bas de la page.

![Pour commencer, accédez à la page Paramètres Authentification de sécurité dans l’](assets/compliance-resources-1.png)

## Processus {#process}

[!DNL Marketo Measure] L’authentification unique nécessite de configurer vos paramètres d’authentification en une série d’étapes afin de ne pas risquer de ne plus pouvoir vous connecter à votre compte [!DNL Marketo Measure].

Configurez l’application [!DNL Marketo Measure] dans votre fournisseur d’identité. Consultez la documentation externe répertoriée ci-dessous pour les procédures.

    a. Lorsqu’on vous demande l’URL d’authentification unique, l’URL de personne destinataire, l’URL de destination ou l’URL d’ACS (Assertion Customer Service) SAML, utilisez [https://apps.bizible.com/BizibleSAML2/ReceiveSSORequest](https://apps.bizible.com/BizibleSAML2/ReceiveSSORequest).
    
    b. Lorsqu’on vous demande l’URL de restriction d’audience ou l’identifiant unique défini par l’application, utilisez [https://BizibleLPM](https://biziblelpm/).

Basculer vers la SSO personnalisée dans l’application [!DNL Marketo Measure]

    a. Une fois que le groupe de facturation a été activé pour votre compte, vous pouvez accéder à [!UICONTROL Paramètres] > [!UICONTROL Sécurité] > [!UICONTROL Authentification]
    
    .b. Par défaut, votre type de connexion sera défini sur « Utilisateurs et utilisatrices CRM ».
    
    c. Définissez le type de connexion sur « SSO personnalisée » pour commencer le processus de configuration.

Renseigner les paramètres de connexion pour la configuration de votre fournisseur d’identité

    a. Votre fournisseur d’identité peut fournir un document .xml de métadonnées IdP qui extrait les champs de configuration requis. Chargez le contenu du document .xml ou renseignez les trois champs ci-dessous à partir des résultats obtenus lors du processus de configuration du fournisseur d’identité. **Il est inutile de faire les deux.**
    
    i. URL d’IdP : l’URL vers laquelle  [!DNL Marketo Measure]  doit pointer pour authentifier vos utilisateurs et utilisatrices dans l’application  [!DNL Marketo Measure] . Parfois appelée « URL de redirection ».
    ii. IdP émetteur : identifiant unique du fournisseur d’identité. Parfois appelée « clé externe ».
    iii. Certificat d’IdP : clé publique qui permet à  [!DNL Marketo Measure]  de vérifier et de valider la signature de toutes les réponses du fournisseur d’identité.

Définissez l’expiration du jeton pour vos utilisateurs et utilisatrices en minutes.

    a.  [!DNL Marketo Measure]  autorise un nombre entier de 1 à 1 440 minutes. Lorsque le temps de session d’une personne a été dépassé, elle est déconnecté dès qu’elle navigue vers une nouvelle page.

Configurez et mappez vos attributs d’utilisateur ou d’utilisatrice au prénom, au nom et à l’adresse e-mail correspondants.

    a. En saisissant les attributs SAML,  [!DNL Marketo Measure]  sera en mesure de reconnaître vos utilisateurs et utilisatrices grâce aux informations transmises.
    
    i. Attribut de l’adresse e-mail : indiquez le nom de l’attribut que votre fournisseur d’identité utilise pour l’adresse e-mail de l’utilisateur ou de l’utilisatrice.
    ii. Attribut du prénom : indiquez le nom de l’attribut que votre fournisseur d’identité utilise pour le prénom de l’utilisateur ou de l’utilisatrice.
    iii. Attribut du nom : indiquez le nom de l’attribut que votre fournisseur d’identité utilise pour le nom de l’utilisateur ou de l’utilisatrice.
    
    b. Conseil : si vous testez votre configuration SAML maintenant, nous analyserons les attributs E-mail, Prénom et Nom que vous pouvez utiliser dans cette section.

![b. Conseil : si vous testez votre configuration SAML maintenant, nous allons analyser](assets/discover-control-1.png)

Configurez et mappez vos paramètres de rôle d’utilisateur et d’utilisatrice aux rôles ou groupes correspondants classés par votre IdP.

    a. Les clientes et clients ont la possibilité d’attribuer aux utilisateurs et utilisatrices  [!DNL Marketo Measure]  des rôles basés sur les groupes définis dans leur fournisseur d’identité. En saisissant vos attributs SAML,  [!DNL Marketo Measure]  sera en mesure de mapper les rôles et les groupes de vos utilisateurs et utilisatrices  [!DNL Marketo Measure]  à leurs autorisations. Nous vous recommandons vivement de configurer ces rôles afin que votre administrateur ou administratrice  [!DNL Marketo Measure]  dispose de droits suffisants pour mettre à jour votre compte.
    
    b. Si aucun rôle ou groupe n’est mappé, le paramètre par défaut est que toutes les personnes employées du fournisseur d’identité auront un accès d’utilisation standard.
    
    i. Utilisateur ou utilisatrice standard  [!DNL Marketo Measure]  : indiquez la valeur du rôle ou du groupe (de votre fournisseur de SSO) pour les utilisateurs et utilisatrices qui doivent avoir un accès en lecture seule à l’application  [!DNL Marketo Measure] .
    ii. [!DNL Marketo Measure] Utilisateur administrateur ou utilisatrice administratrice de compte : indiquez la valeur du rôle ou du groupe (de votre fournisseur de SSO) pour les utilisateurs et utilisatrices qui doivent avoir un accès administratif à l’application  [!DNL Marketo Measure] . Cela signifie que le rôle dispose d’un accès de modification des configurations et des paramètres liés à votre compte.
    iii. Vous devez avoir un attribut dans votre IdP avec le nom exact « groups » qui contient les valeurs que vous avez mises dans les attributs « Bizible Standard User » (Utilisateur ou utilisatrice standard Bizible) ou « Bizible Account Admin User » (Utilisateur administrateur ou utilisatrice administratrice Bizible).
    
    c. Si plusieurs rôles ou groupes doivent être mappés à un rôle, saisissez chaque valeur en la séparant par une virgule.

![c. Si plusieurs rôles ou groupes doivent être mappés à un rôle ](assets/discover-control-2.png)

Tester la configuration de l’authentification unique

    a. Avant de pouvoir cliquer sur Enregistrer, vous devrez cliquer sur le bouton [!UICONTROL Tester l’authentification SAML] pour vérifier que vos paramètres ont été configurés correctement.
    
    b. Si vous voyez une erreur « failure » (échec), suivez le message et réessayez.

![b. Si une erreur d’échec s’affiche, suivez le message et tentez ](assets/discover-control-3.png)

Enregistrez vos paramètres et demandez à vos collègues d’utiliser l’[!UICONTROL Authentification unique] avec votre nouvelle URL de connexion personnalisée.

    a. Important : une fois que vous aurez enregistré vos nouveaux paramètres d’authentification, il est possible que votre session se termine lorsque vous naviguez vers une nouvelle page parce que vous avez désactivé la connexion des utilisateurs et utilisatrices CRM et activé la SSO personnalisée.

![a. Important : une fois que vous avez enregistré vos nouveaux paramètres d’authentification, cela devient possible](assets/discover-control-3.png)

Essayez donc.

    a. Utilisez votre nouvelle URL de connexion personnalisée et essayez de vous reconnecter à l’application  [!DNL Marketo Measure]  avec les informations d’identification de votre fournisseur d’identité.
    
    b. Le format ressemble à « https://apps.adobe.com/business/[accountName] »
    
    c. Félicitations. Vous avez configuré avec succès l’authentification unique dans l’application  [!DNL Marketo Measure]  pour votre compte.

![c. Félicitations ! Vous avez correctement configuré l&#39;authentification SSO dans ](assets/discover-control-3.png)

>[!NOTE]
>
>Après avoir configuré la SSO, vous n’avez plus besoin d’ajouter des utilisateurs et des utilisatrices dans l’application [!DNL Marketo Measure]. L’approvisionnement des utilisateurs et utilisatrices doit être géré directement dans votre fournisseur d’identité.

## Utilisateurs et utilisatrices CRM (configuration avancée) {#crm-users-advanced-setup}

Par défaut, tous les comptes peuvent accéder à l’application [!DNL Marketo Measure] en utilisant leurs informations d’identification CRM. Parfois, les personnes propriétaires de comptes doivent limiter l’accès à certains rôles et ne pas l’autoriser à tous les utilisateurs et utilisatrices disposant d’une licence CRM active. La configuration avancée vous permet de mapper vos rôles et groupes CRM aux autorisations des utilisateurs et des utilisatrices [!DNL Marketo Measure].

Si aucun rôle ou groupe n’est mappé, le paramètre par défaut est que toutes les licences actives dans votre CRM ont un accès utilisateur ou utilisatrice standard.

* Utilisateur ou utilisatrice standard [!DNL Marketo Measure] : indiquez la valeur du rôle ou du groupe pour les utilisateurs et utilisatrices qui doivent avoir un accès en lecture seule à l’application [!DNL Marketo Measure].
* Utilisateur administrateur ou utilisatrice administratrice de compte [!DNL Marketo Measure] : indiquez la valeur du rôle ou du groupe pour les utilisateurs et utilisatrices qui doivent avoir un accès administratif à l’application [!DNL Marketo Measure]. Cela signifie que le rôle dispose d’un accès de modification des configurations et des paramètres liés à votre compte.

Si plusieurs rôles ou groupes doivent être mappés à un rôle, saisissez chaque valeur en la séparant par une virgule.

**Rôles Salesforce**

Pour les rôles [!DNL Salesforce], utilisez le nom de chaque rôle. Tous les rôles se trouvent dans le menu [!UICONTROL Configuration] > [!UICONTROL Gérer les utilisateurs et utilisatrices] > [!UICONTROL Rôles].

![Pour les rôles Salesforce, utilisez le nom de chaque rôle. Tous les rôles](assets/discover-control-3.png)

**Rôles Dynamics**

Pour les rôles [!DNL Dynamics], utilisez le nom de chaque rôle de sécurité. Tous les rôles de sécurité se trouvent dans le menu [!UICONTROL Paramètres] > [!UICONTROL Sécurité] > [!UICONTROL Rôles de sécurité].

![Pour les rôles Dynamics, utilisez le nom de chaque rôle de sécurité. Tous](assets/discover-control-3.png)

![Pour les rôles Dynamics, utilisez le nom de chaque rôle de sécurité. Tous](assets/discover-control-3.png)

**Utilisateurs et utilisatrices Google**

Une fois la SSO personnalisée configurée, la page [!UICONTROL Utilisateurs et utilisatrices] est mise à jour pour n’afficher que les utilisateurs et utilisatrices externes qui ont été ajoutés avec des identifiants Google. Étant donné que tous les utilisateurs et utilisatrices disposant d’un accès sont définis par la configuration SSO, d’autres utilisateurs et utilisatrices externes sont répertoriés ici.

![Une fois la connexion unique personnalisée configurée, la page Utilisateurs est la suivante ](assets/discover-control-3.png)

Seuls des comptes [!DNL Google] valides peuvent être ajoutés et doivent avoir un rôle d’utilisateur ou d’utilisatrice défini.

## Liens externes {#external-links}

* [Okta](https://developer.okta.com/standards/SAML/setting_up_a_saml_application_in_okta)
* [Ping Identity](https://docs.pingidentity.com:443/bundle/p1_enterpriseConfigSsoSaml_cas/page/enableAppWithoutURL.html)
* [OneLogin](https://onelogin.service-now.com/support?id=kb_article&sys_id=b2c91143db109700d5505eea4b9619d5)
* [Active Directory](https://docs.microsoft.com/fr-fr/azure/active-directory/active-directory-saas-custom-apps)
