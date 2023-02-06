---
unique-page-id: 18874795
description: Ajouter [!DNL Marketo Measure] Script - [!DNL Marketo Measure] - Documentation du produit
title: Ajouter [!DNL Marketo Measure] Script
exl-id: f8773037-04d7-4308-ba04-440e9b990d92
source-git-commit: 82cc8269bfdb26b6acf039d0ce0e06564f5e2612
workflow-type: tm+mt
source-wordcount: '1307'
ht-degree: 0%

---

# Ajouter [!DNL Marketo Measure] Script {#adding-marketo-measure-script}

[!DNL Marketo Measure] JavaScript par lequel vous souhaitez effectuer un suivi [!DNL Marketo Measure] doit être ajouté à toutes les propriétés web dès que possible. Une fois le JavaScript déployé, [!DNL Marketo Measure] commencera à collecter vos données numériques. Cet article décrit les méthodes de déploiement [!DNL Marketo Measure] JavaScript et autres considérations à prendre en compte.

>[!NOTE]
>
>Assurez-vous que vous avez [ont revendiqué tous les domaines appropriés dans la variable [!DNL Adobe Admin Console]](/help/marketo-measure-and-adobe/domain-management.md){target="_blank"} en plus du déploiement de la variable [!DNL Marketo Measure] JavaScript.

Prise en main de [!DNL Marketo Measure], vous pouvez ajouter le [!DNL Marketo Measure] JavaScript sur votre site web :

* Codage en dur
* Systèmes Tag Management

## Codage en dur {#hard-coding}

Il est recommandé d’utiliser un codage en dur. [!DNL Marketo Measure] JavaScript pour vos propriétés web. Pour coder en dur le script, vous devez placer le script avant la fermeture de la `</head>` sur chaque page de votre site.

`<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>`

Codage du code JavaScript dans le `<head>` de vos pages, vous avez la garantie que [!DNL Marketo Measure] Le script se charge en premier et les informations de référence ne sont pas manquantes. Le [!DNL Marketo Measure] JavaScript se charge de manière asynchrone. En cas de codage en dur, le code JavaScript doit être ajouté manuellement à l’automatisation du marketing.

>[!TIP]
>
>Découvrez comment vous assurer que votre script est [Conformité au RGPD](/help/security-and-compliance/compliance-related-resources/ensuring-consent-for-gdpr-in-marketo-measure-js.md){target="_blank"}.

## Systèmes Tag Management {#tag-management-systems}

Si vous ajoutez [!DNL Marketo Measure] Il n’est pas possible d’utiliser du code JavaScript en dur, mais une autre option consiste à ajouter le paramètre [!DNL Marketo Measure] script utilisant un système Tag Management, tel que [!DNL Google Tag Manager] (GTM) ou Tealium.

Notez que l’utilisation des systèmes de gestion des balises pour le déploiement [!DNL Marketo Measure] JS peut entraîner une perte de données potentielle de 5 à 10 % en raison de la latence de chargement du script. Essentiellement, si l’outil de gestion des balises ne se charge pas assez rapidement, [!DNL Marketo Measure] JS ne peut pas non plus se charger suffisamment rapidement et peut perdre les informations du premier référent.

Une pratique courante consiste à déployer [!DNL Marketo Measure] JS via un outil de gestion des balises jusqu’à ce que le minutage/l’approvisionnement soit préférable pour passer au codage en dur.

Pour ajouter [!DNL Marketo Measure] via une solution de gestion des balises, vous devez créer une balise et y ajouter votre code JavaScript. Appliquez cette balise à toutes les pages de votre site web dont vous souhaitez effectuer le suivi.

[!DNL Marketo Measure] recommande que toute page vue provoque le déclenchement de la balise . De plus, il est préférable de donner [!DNL Marketo Measure] priorité la plus élevée dans l’ordre de déclenchement et assurez-vous qu’il n’y a pas de scripts synchrones devant la balise [!DNL Marketo Measure] afin d’assurer la qualité des données la plus élevée.

Plus d’informations peuvent être [ici](/help/marketo-measure-tracking/setting-up-tracking/adding-marketo-measure-script-via-google-tag-manager.md){target="_blank"}.

## Remarques supplémentaires {#additional-considerations}

[!DNL Marketo Measure] JavaScript est basé sur des domaines. Il peut donc gérer automatiquement tous les sous-domaines tant que le code JavaScript se trouve sur les pages et que le domaine racine est identique au domaine utilisé pour créer le compte Marketo Measure.

Cependant, si vous utilisez des domaines distincts ou internationaux, veillez à laisser votre [!DNL Marketo Measure] Connaître. Le ou les domaines doivent être ajoutés manuellement à votre compte sur la page [!DNL Marketo Measure] terminer de sorte que [!DNL Marketo Measure] sait lier les données des domaines supplémentaires à votre compte. Par conséquent, veuillez envoyer tous les domaines distincts/internationaux à votre [!DNL Marketo Measure] Consultant.

Si vous utilisez des pages tierces, discutez de votre cas d’utilisation avec votre [!DNL Marketo Measure] Consultant. En général, vous devez savoir si vous pouvez ajouter une version personnalisée de [!DNL Marketo Measure] JavaScript pour effectuer le suivi de ces pages, le cas échéant. Si cela n’est pas possible, le suivi via les points de contact de Campaign CRM sera exploré avec votre [!DNL Marketo Measure] Consultant.

Les formulaires ne doivent-ils PAS être suivis par [!DNL Marketo Measure] puisqu’ils n’ont pas nécessairement de sens pour l’attribution (par exemple, désabonner des formulaires, connexions client, etc.) ? Si tel est le cas, vous souhaiterez ajouter le code d’exclusion [dans cet article](/help/marketo-measure-tracking/setting-up-tracking/excluding-marketo-measure-from-specific-forms.md){target="_blank"} à chaque formulaire

Avez-vous des pages non sécurisées ? Si tel est le cas, vous souhaitez les sécuriser, car la navigation entre une page sécurisée/non sécurisée interrompt la session de suivi.

Assurez-vous d’avoir une conversation avec votre équipe web pour qu’elle sache [!DNL Marketo Measure] JavaScript doit toujours se trouver sur les propriétés web appropriées. Si de nouvelles pages/formulaires/sites sont introduits, assurez-vous de déployer [!DNL Marketo Measure] JavaScript fait partie du protocole .

Si une [!DNL Web Application Firewall (WAF)] est déclenché lors de la configuration de JavaScript, les utilisateurs peuvent désactiver cette règle WAF ou placer sur la liste autorisée les cookies, comme dans l’exemple ci-dessous :

![](assets/adding-marketo-measure-script-1.png)

## Forms doit accorder plus d’attention à {#forms-to-pay-extra-attention-to}

**Envoi de plusieurs formulaires**

* Problème : Si plusieurs formulaires liés font partie d’un seul envoi de formulaire, il est possible que le premier formulaire génère un point de contact même si le formulaire complet n’est pas envoyé.
* Solution : Vous devrez forcer l’un des formulaires à signaler à l’utilisateur. [!DNL Marketo Measure] en fonction des données mises en cache et discutez des pratiques d’abandon. En général, [code utilisateur du rapport](/help/marketo-measure-tracking/setting-up-tracking/adding-marketo-measure-script-to-different-form-providers/ajax-form-handling.md){target="_blank"} peut résoudre ce problème.

**Connexion au compte (pas création)**

* Problème : [!DNL Marketo Measure] recommande de ne pas créer de points de contact pour les connexions de compte suivantes, car ceux-ci tendent à diluer l’article d’attribution.
* Solution : Ajoutez le code d’exclusion au formulaire de connexion du compte/client/partenaire.

>[!NOTE]
>
>Il est recommandé de créer un point de contact pour la création d’un compte ou d’un essai.

**Téléchargement de la ressource**

* Problème : Si vos ressources sont sécurisées, [!DNL Marketo Measure] effectue le suivi des téléchargements à mesure que le formulaire se remplit. Si vos ressources ne sont pas sécurisées, il existe des limites à ce sur quoi nous pouvons créer des rapports sans personnalisation.
* Solution : Obtenez la ressource si vous souhaitez qu’elle soit suivie par [!DNL Marketo Measure] JavaScript. S’il ne s’agit pas d’une option et que vous souhaitez toujours un point de contact, envisagez plutôt de synchroniser une campagne CRM.

**iFrames**

* Problème : Les iFrames fonctionnent essentiellement comme des pages dans les pages.
* Solution : Le [!DNL Marketo Measure] JS doit être déployé directement dans l’en-tête de l’iFrame pour que nous puissions le joindre correctement au formulaire.

**Lightbox**

* Les Lightbox sont généralement des fenêtres contextuelles qui contiennent des iFrames.
* Solution : la valeur [!DNL Marketo Measure] Les fichiers JS doivent être déployés dans l’en-tête de cet iFrame hébergé.

**Plusieurs formulaires sur une page**

* Problème : S’il existe plusieurs formulaires hébergés sur une page, vous ne pourrez peut-être pas savoir quel formulaire spécifique a été rempli avec la variable [!DNL Marketo Measure] Champ URL du formulaire.
* Solution : Si vous devez savoir quel formulaire a été rempli, essayez de configurer le hachage dynamique des URL avec votre équipe web.

**Forms organisé en `<div>` format**

* Problème : [!DNL Marketo Measure] JS a du mal à reconnaître les formulaires organisés dans `<div>` format afin que le code personnalisé puisse être nécessaire.
* Solution : Ces [modèles d’utilisateurs de rapports](/help/marketo-measure-tracking/setting-up-tracking/adding-marketo-measure-script-to-different-form-providers/ajax-form-handling.md){target="_blank"} peut être utilisé par votre équipe de développement web pour ajouter le code nécessaire.

**Chat**

* Problème : Si vous utilisez un fournisseur de chat, une gestion spéciale peut être requise.
* Solution : [!DNL Marketo Measure] s’intègre à Drift, Olark, Livechat, LivePerson et SnapEngageEngage. Toutes les autres plates-formes doivent être suivies par le biais de l’adhésion aux campagnes CRM.

**Second domaine**

* Problème : [!DNL Marketo Measure] JavaScript est spécifique au domaine. Des étapes supplémentaires doivent donc être effectuées pour les domaines distincts ou internationaux. Notez que [!DNL Marketo Measure] JS peut gérer les sous-domaines sur le même domaine racine.
* Solution : Si vous possédez plusieurs domaines racine, vous souhaitez que le suivi soit effectué par [!DNL Marketo Measure] veillez à ajouter JS aux domaines ET laissez votre [!DNL Marketo Measure] Le conseiller sait quels domaines doivent être associés manuellement à votre [!DNL Marketo Measure] compte .

## Tests [!DNL Marketo Measure] JavaScript {#testing-marketo-measure-javascript}

Votre [!DNL Marketo Measure] Le consultant vous aidera à tester le site web pour vous assurer que [!DNL Marketo Measure] JavaScript est présent sur toutes les pages. Une partie de ce test consiste à envoyer quelques formulaires remplis avec des détails de test clairement indiqués afin de s’assurer que le suivi renvoie correctement.

Cependant, votre [!DNL Marketo Measure] Il est probable que votre conseiller ne soit pas aussi familier avec votre site web qu’avec votre équipe. C’est pourquoi il est très important que votre équipe web ou toute autre équipe appropriée vérifie minutieusement le site web, en particulier s’il existe des formulaires complexes en cours d’utilisation comme ceux mentionnés ci-dessus. Votre équipe sera chargée, au bout du compte, de vous assurer que toutes les propriétés web nécessaires font l’objet d’un suivi correct. Toutefois, si vous connaissez des formulaires ou des situations complexes, vous êtes invité à contacter votre [!DNL Marketo Measure] Consultant pour obtenir de l’aide sur les tests.

Pour tester vous-même un formulaire, procédez comme suit :

1. Utilisez toujours un navigateur incognito ou effacez le cache entre chaque test d’envoi de formulaire ET utilisez une adresse électronique différente à chaque fois.

   a. Une bonne pratique consiste à utiliser un faux email contenant un élément indiquant qu’il s’agit d’un test et l’heure de la journée. Par exemple : testing830am@test.com.

1. Enregistrez l’URL de la page que vous envoyez le formulaire et l’email utilisé.

1. Recherchez l’enregistrement créé dans votre CRM (prospect ou contact) pour cet envoi de formulaire et vérifiez qu’un point de contact a été correctement créé.

   a. Vous pouvez utiliser une [!DNL Marketo Measure] rapport d’inventaire, tel que Pistes avec points de contact de l’acheteur, ou examinez la mise en page de piste/contact si vous avez choisi de mettre à jour vos mises en page avec [!DNL Marketo Measure] détails.

   b. Notez que le traitement des données peut prendre du temps.
