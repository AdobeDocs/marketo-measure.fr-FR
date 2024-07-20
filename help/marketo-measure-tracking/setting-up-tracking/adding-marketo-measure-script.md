---
unique-page-id: 18874795
description: Ajout de [!DNL Marketo Measure] Script - [!DNL Marketo Measure]
title: Ajout d’un script  [!DNL Marketo Measure]
exl-id: f8773037-04d7-4308-ba04-440e9b990d92
feature: Tracking
source-git-commit: 9e672d0c568ee0b889461bb8ba6fc6333edf31ce
workflow-type: tm+mt
source-wordcount: '1282'
ht-degree: 57%

---

# Ajout d’un script [!DNL Marketo Measure] {#adding-marketo-measure-script}

Le code JavaScript [!DNL Marketo Measure] que vous souhaitez suivre grâce à [!DNL Marketo Measure] doit être ajouté à toutes les propriétés web dès que possible. Une fois JavaScript déployé, [!DNL Marketo Measure] commence à collecter vos données numériques. Cet article décrit les méthodes de déploiement de [!DNL Marketo Measure] JavaScript et des considérations supplémentaires.

>[!NOTE]
>
>Assurez-vous que vous avez [revendiqué tous les domaines appropriés dans  [!DNL Adobe Admin Console]](/help/marketo-measure-and-adobe/domain-management.md){target="_blank"} en plus du déploiement du code JavaScript [!DNL Marketo Measure].

Lors de la prise en main de [!DNL Marketo Measure], vous pouvez ajouter le code JavaScript [!DNL Marketo Measure] sur votre site web de deux manières :

* Codage en dur
* Systèmes de gestion des balises

## Codage en dur {#hard-coding}

Une bonne pratique consiste à coder en dur le code JavaScript [!DNL Marketo Measure] dans vos propriétés web. Pour coder en dur le script, vous devez placer le script avant la fermeture `</head>` sur chaque page de votre site.

`<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>`

Le codage forcé du JavaScript dans le `<head>` de vos pages garantit que le script [!DNL Marketo Measure] se charge en premier et que les informations de référence ne sont pas manquantes. Le code JavaScript [!DNL Marketo Measure] se charge de manière asynchrone. En cas de codage en dur, le code JavaScript doit être ajouté manuellement à l’automatisation du marketing.

>[!TIP]
>
>Découvrez comment vous assurer que votre script est [conforme au RGPD](/help/security-and-compliance/compliance-related-resources/ensuring-consent-for-gdpr-in-marketo-measure-js.md){target="_blank"}.

## Systèmes de gestion des balises {#tag-management-systems}

Si l’ajout de [!DNL Marketo Measure] JavaScript par codage dur n’est pas possible, une autre option consiste à ajouter le script [!DNL Marketo Measure] à l’aide d’un système Tag Management tel que [!DNL Google Tag Manager] (GTM) ou Tealium.

L’utilisation de systèmes de gestion des balises pour déployer [!DNL Marketo Measure] JS peut entraîner une perte de données potentielle de 5 à 10 % en raison de la latence de chargement du script. Essentiellement, si l’outil de gestion des balises ne se charge pas assez rapidement, le code JS [!DNL Marketo Measure] ne peut pas non plus se charger suffisamment rapidement et peut perdre les informations du premier référent.

Une pratique courante consiste à déployer le code JS [!DNL Marketo Measure] via un outil de gestion des balises jusqu’à ce que le temps/les ressources permettent de passer au codage en dur.

Pour ajouter un script [!DNL Marketo Measure] via une solution de gestion des balises, vous devez créer une balise et y ajouter notre JavaScript. Appliquez cette balise à toutes les pages de votre site web dont vous souhaitez effectuer le suivi.

[!DNL Marketo Measure] recommande que toute page vue provoque le déclenchement de la balise. En outre, il est préférable de donner à [!DNL Marketo Measure] la priorité la plus élevée dans l’ordre de déclenchement et de s’assurer qu’il n’y a aucun script synchrone devant la balise [!DNL Marketo Measure] pour garantir la qualité de données la plus élevée.

Vous trouverez de plus amples informations [ici](/help/marketo-measure-tracking/setting-up-tracking/adding-marketo-measure-script-via-google-tag-manager.md){target="_blank"}.

## Remarques supplémentaires {#additional-considerations}

Le code JavaScript [!DNL Marketo Measure] est basé sur des domaines. Il peut donc gérer automatiquement tous les sous-domaines tant que le code JavaScript se trouve sur les pages et que le domaine racine est identique au domaine utilisé pour créer le compte Marketo Measure.

Cependant, si vous utilisez des domaines distincts ou internationaux, veillez à en informer votre conseiller ou votre conseillère [!DNL Marketo Measure]. Les domaines doivent être ajoutés manuellement à votre compte à la fin [!DNL Marketo Measure] afin que [!DNL Marketo Measure] sache lier les données des domaines supplémentaires à votre compte. Ainsi, envoyez tous les domaines distincts/internationaux à votre consultant [!DNL Marketo Measure].

Si vous utilisez des pages tierces, discutez de votre cas d’utilisation avec votre consultant [!DNL Marketo Measure]. En général, vous devez savoir si vous pouvez ajouter une version personnalisée de [!DNL Marketo Measure] JavaScript pour effectuer le suivi de ces pages, le cas échéant. Si cela n&#39;est pas possible, le suivi via les points de contact de Campaign CRM sera exploré avec votre consultant [!DNL Marketo Measure].

Avez-vous des formulaires qui ne doivent PAS être suivis par [!DNL Marketo Measure] car ils n’ont pas nécessairement de sens pour l’attribution (par exemple, les formulaires de désabonnement, les connexions client, etc.) ? Si c&#39;est le cas, vous souhaiterez ajouter le code d&#39;exclusion [ de cet article ](/help/marketo-measure-tracking/setting-up-tracking/excluding-marketo-measure-from-specific-forms.md){target="_blank"} à chaque formulaire.

Avez-vous des pages non sécurisées ? Vous devez les sécuriser, car la navigation entre une page sécurisée/non sécurisée rompt la session de suivi.

Assurez-vous d’avoir une conversation avec votre équipe web pour qu’elle sache que le code JavaScript [!DNL Marketo Measure] doit toujours se trouver sur les propriétés web appropriées. Si de nouvelles pages/formulaires/sites sont introduits, assurez-vous que le déploiement du code JavaScript [!DNL Marketo Measure] fait partie du protocole.

Si un avertissement [!DNL Web Application Firewall (WAF)] est déclenché lors de la configuration de JavaScript, les utilisateurs peuvent désactiver cette règle WAF ou placer sur la liste autorisée les cookies, comme dans l’exemple ci-dessous :

![](assets/adding-marketo-measure-script-1.png)

## Formulaires auxquels prêter une attention particulière {#forms-to-pay-extra-attention-to}

**Envoi de plusieurs formulaires**

* Problème : si plusieurs formulaires liés font partie d’un seul envoi de formulaire, il est possible que le premier formulaire génère un point de contact même si le formulaire complet n’est pas envoyé.
* Solution : vous devez forcer l’un des formulaires à signaler l’utilisateur à [!DNL Marketo Measure] en fonction des données mises en cache et discuter des pratiques d’abandon. En général, le [code utilisateur du rapport](/help/marketo-measure-tracking/setting-up-tracking/adding-marketo-measure-script-to-different-form-providers/ajax-form-handling.md){target="_blank"} peut résoudre ce problème.

**Connexion au compte (et non pas la création)**

* Problème : [!DNL Marketo Measure] recommande de ne pas créer de points de contact pour les connexions ultérieures au compte, car ceux-ci tendent à diluer la story d’attribution.
* Solution : ajoutez le code d’exclusion au formulaire de connexion du compte/client/partenaire.

>[!NOTE]
>
>Il est recommandé de créer un point de contact pour la création d’un compte ou d’un essai.

**Téléchargement de la ressource**

* Problème : si vos ressources sont sécurisées, [!DNL Marketo Measure] effectue le suivi des téléchargements en tant que remplissage de formulaire. Si vos ressources ne sont pas sécurisées, les éléments pour lesquels nous pouvons créer des rapports sans personnalisation sont limités.
* Solution : sécurisez la ressource si vous souhaitez qu’elle soit suivie par le code JavaScript [!DNL Marketo Measure]. Si ce n’est pas possible, mais que vous souhaitez tout de même un point de contact, envisagez plutôt de synchroniser une campagne CRM.

**iFrames**

* Problème : les iFrames fonctionnent essentiellement comme des pages dans les pages.
* Solution : le fichier JS [!DNL Marketo Measure] doit être déployé directement dans l’en-tête de l’iFrame pour que nous le joignions correctement au formulaire.

**Lightbox**

* Les lightbox sont généralement des fenêtres contextuelles qui contiennent des iFrames
* Solution : le code JS [!DNL Marketo Measure] doit être déployé dans l’en-tête de cet iFrame hébergé.

**Plusieurs formulaires sur une page**

* Problème : s’il existe plusieurs formulaires hébergés sur une page, vous ne pourrez peut-être pas savoir quel formulaire spécifique a été rempli avec le champ URL du formulaire [!DNL Marketo Measure].
* Solution : si vous devez savoir quel formulaire a été rempli, essayez de configurer le hachage dynamique des URL avec votre équipe web.

**Formulaires organisés au format `<div>`**

* Problème : le code JS [!DNL Marketo Measure] a du mal à reconnaître les formulaires organisés au format `<div>`. Un code personnalisé peut être nécessaire.
* Solution : ces [modèles d’utilisateurs de rapports](/help/marketo-measure-tracking/setting-up-tracking/adding-marketo-measure-script-to-different-form-providers/ajax-form-handling.md){target="_blank"} peuvent être utilisés par votre équipe de développement web pour ajouter le code nécessaire.

**Messagerie instantanée**

* Problème : si vous utilisez un fournisseur de chat, une gestion spéciale peut être requise.
* Solution : [!DNL Marketo Measure] s’intègre à Drift, Olark, Livechat, LivePerson et SnapEngage. Toutes les autres plateformes doivent être suivies par le biais de l’abonnement aux campagnes CRM.

**Deuxième domaine**

* Problème : [!DNL Marketo Measure] JavaScript est spécifique au domaine. Des étapes supplémentaires doivent donc être effectuées pour les domaines distincts ou internationaux. [!DNL Marketo Measure] JS peut gérer les sous-domaines sur le même domaine racine.
* Solution : si vous possédez plusieurs domaines racine, et que vous souhaitez effectuer le suivi par [!DNL Marketo Measure], veillez à ajouter le code JS aux domaines ET informer votre conseiller ou votre conseillère [!DNL Marketo Measure] des domaines qui doivent être associés manuellement à votre compte [!DNL Marketo Measure].

## Test du code JavaScript [!DNL Marketo Measure] {#testing-marketo-measure-javascript}

Votre consultant [!DNL Marketo Measure] vous aidera à tester le site web afin de vous assurer que [!DNL Marketo Measure] JavaScript est présent sur toutes les pages. Une partie de ce test consiste à envoyer quelques champs de formulaire avec des détails de test clairement indiqués afin de s’assurer que le suivi renvoie correctement.

Cependant, il est probable que votre conseiller ou votre conseillère [!DNL Marketo Measure] ne soit pas aussi à l’aise avec votre site web que votre équipe. C’est pourquoi il est très important que votre équipe web ou toute autre équipe appropriée vérifie minutieusement le site web, en particulier s’il existe des formulaires complexes en cours d’utilisation comme ceux mentionnés ci-dessus. Votre équipe sera chargée de veiller à ce que toutes les propriétés web nécessaires fassent l’objet d’un suivi correct. Toutefois, si vous faites face à des formulaires ou des situations complexes, vous pouvez contacter votre conseiller ou votre conseillère [!DNL Marketo Measure] pour qu’il ou elle vous aide avec les tests.

Pour tester vous-même un formulaire, procédez comme suit :

1. Utilisez toujours un navigateur incognito ou effacez le cache entre chaque test d’envoi de formulaire ET utilisez une adresse e-mail différente à chaque fois.

   a. Une bonne pratique consiste à utiliser une fausse adresse e-mail contenant un élément indiquant qu’il s’agit d’un test ainsi que l’heure. Par exemple : testing830am@test.com.

1. Enregistrez l’URL de la page que vous envoyez le formulaire et l’adresse électronique utilisée.

1. Recherchez l’enregistrement créé dans votre CRM (prospect ou contact) pour cet envoi de formulaire et vérifiez qu’un point de contact a été créé.

   a. Vous pouvez utiliser un rapport d’inventaire [!DNL Marketo Measure], tel que Prospects avec Buyer Touchpoints, ou examiner la disposition de la page de prospect/contact si vous avez choisi de mettre à jour vos dispositions de pages avec les détails [!DNL Marketo Measure].

   b. Le traitement des données peut prendre du temps.
