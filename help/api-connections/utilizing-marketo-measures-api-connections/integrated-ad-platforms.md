---
unique-page-id: 18874594
description: Plateformes d’annonces intégrées - [!DNL Marketo Measure]
title: Plateformes publicitaires intégrées
exl-id: df30ee8a-8b07-4f14-94e8-cc482fca8b18
feature: APIs, Integration
source-git-commit: 48962b999fdd16fe96d18708ec301e64a39bc76e
workflow-type: tm+mt
source-wordcount: '1675'
ht-degree: 0%

---

# Plateformes publicitaires intégrées {#integrated-ad-platforms}

[!DNL Marketo Measure] possède des connexions API avec Google AdWords, Microsoft BingAds, [!DNL Facebook] Ads et DoubleClick Campaign Manager. Grâce à ces connexions API, [!DNL Marketo Measure] peut facilement extraire des données et les transmettre à votre CRM avec l’application externe Buyer. Aucun chargement manuel des coûts ou des données n’est requis. Au contraire, vos comptes doivent simplement être connectés et autorisés à l’application [!DNL Marketo Measure]. [!DNL Marketo Measure] téléchargera alors automatiquement vos coûts marketing à partir des plateformes et les chargera dans l’application [!DNL Marketo Measure]. Si vous choisissez d’activer le balisage automatique pour AdWords, BingAds ou [!DNL Facebook] Ads, [!DNL Marketo Measure] ajoutera automatiquement ses paramètres aux URL de vos publicités.

## Comment connecter des plateformes d’annonces publicitaires {#how-to-connect-ad-platforms}

Avant d&#39;entrer dans les détails de chaque plateforme, nous allons passer en revue la manière de connecter l&#39;un de ces comptes à [!DNL Marketo Measure]. Connectez-vous d’abord à l’application [!DNL Marketo Measure] et accédez à l’option **[!UICONTROL Paramètres]** sous l’onglet **[!UICONTROL Mon compte]** en haut à gauche de l’écran. Sélectionnez ensuite **[!UICONTROL Connexions]** sous la section **[!UICONTROL Intégrations]** sur la gauche.

Comme illustré ci-dessous, un bouton s’affiche pour configurer de nouvelles connexions d’annonces.

![](assets/2.png)

Après avoir cliqué sur le bouton [!UICONTROL Configurer une nouvelle connexion aux publicités] , une fenêtre (illustrée ci-dessous) s’affiche avec quatre types d’icône [!UICONTROL se connecter] . Cliquez sur Se connecter et une autre fenêtre s’affiche pour vous demander des informations d’identification. Saisissez les informations d’identification et cliquez sur [!UICONTROL autoriser] pour connecter le compte à [!DNL Marketo Measure].

![](assets/select-account-type.png)

## Google AdWords {#google-adwords}

Lorsque vous créez vos publicités dans [!DNL Google AdWords], vous êtes invité à baliser vos campagnes de l’une des trois manières suivantes : balisage manuel, balisage automatique ou création d’un modèle de suivi. Le balisage manuel de l’URL d’AdWords repose sur la définition et l’ajout des paramètres à la fin des URL des publicités. Le balisage manuel permet à toute plateforme non Google de lire facilement les données collectées par les paramètres.

Le modèle de suivi est un outil fourni par Google pour ajouter ce qu’il appelle des paramètres ValueTrack. Ils fonctionnent de la même manière que les UTM et d’autres paramètres de balisage.

## Que se passe-t-il lorsque le balisage automatique est activé {#what-happens-when-auto-tagging-is-enabled}

[!DNL Marketo Measure] Recherches de modèles de suivi dans votre compte [!DNL AdWords] :

* *Option A* : Modèle de suivi trouvé. [!DNL Marketo Measure] ajoute ses paramètres au modèle.
* *Option B* : Redirection tierce trouvée. Si une redirection tierce est trouvée dans le modèle de suivi, [!DNL Marketo Measure] ne peut pas effectuer d’action. Vous devrez ajouter manuellement les balises [!DNL Marketo Measure] au système tiers. Un exemple de redirection tierce serait un outil de gestion des offres comme Kenshoo ou Marin. En savoir plus sur l&#39;[impact des outils de gestion des offres [!DNL Marketo Measure]](/help/api-connections/utilizing-marketo-measures-api-connections/how-bid-management-tools-affect-marketo-measure.md){target="_blank"}.

* *Option C* : aucun modèle de suivi n’a été trouvé. [!DNL Marketo Measure] analysera toutes vos URL de destination de l’annonce pour les paramètres [!DNL Marketo Measure]. En fonction de l’analyse, si :
   * Les paramètres sont disponibles : la configuration est terminée.
   * Paramètres introuvables : [!DNL Marketo Measure] ajoute ses paramètres à la fin des URL de destination de l’annonce. [!DNL Marketo Measure] ajoute de nouvelles publicités dans les deux heures qui suivent leur création. Gardez à l’esprit que les paramètres ne seront pas ajoutés à un modèle.

En savoir plus sur notre [[!DNL AdWords] fonctionnalité de balisage automatique](/help/api-connections/utilizing-marketo-measures-api-connections/understanding-marketo-measure-adwords-tagging.md){target="_blank"}.

## Comment activer le balisage automatique pour les mots-clés [!DNL Marketo Measure] {#how-to-enable-marketo-measure-auto-tagging-for-adwords}

Avant d’activer le balisage automatique [!DNL Marketo Measure], **assurez-vous qu’un modèle de suivi est activé au niveau du compte, de la campagne ou du groupe publicitaire dans votre compte Adwords. Ceci est requis pour tout compte AdWords dont le balisage automatique [!DNL Marketo Measure] est activé.** L’activation d’un modèle de suivi empêche toute perte des données de l’historique des performances publicitaires. Notez que l’activation des modèles de suivi au niveau du mot-clé, du lien de site ou de la publicité entraîne la consultation et l’approbation de la publicité et peut potentiellement redémarrer l’historique des performances de vos publicités. Si aucun modèle de suivi n’est activé, [!DNL Marketo Measure] ajoute les paramètres de suivi [!DNL Marketo Measure] directement à l’&quot;URL finale&quot; de la publicité, ce qui peut entraîner une perte des données de l’historique des publicités.

Une fois que vous avez mis en place un modèle de suivi, suivez les instructions ci-dessous pour activer le balisage automatique [!DNL Marketo Measure]. Remarque : [!DNL Marketo Measure] marquera également automatiquement toutes les publicités suspendues dans votre compte.

1. Connectez-vous à votre compte [!DNL Marketo Measure] à l’adresse [experience.adobe.com/marketo-measure](https://experience.adobe.com/marketo-measure){target="_blank"}.

1. Accédez à [!UICONTROL Mon compte] > [!UICONTROL Paramètres] > [!UICONTROL Intégrations] > [!UICONTROL Connexions].

   ![](assets/4.png)

1. Cliquez sur l’icône en forme de crayon en regard du compte Adwords pour activer le balisage automatique [!DNL Marketo Measure].

   ![](assets/5.png)

1. Dans le coin supérieur droit, faites basculer le commutateur **[!UICONTROL d’authentification]** sur **[!UICONTROL Oui]**. Au bas de la page, cliquez sur **[!UICONTROL En savoir plus]** pour développer la zone de texte et cliquez sur **[!UICONTROL Enregistrer]**. La configuration du balisage automatique est terminée.

   ![](assets/6.png)

## Comment configurer un modèle de suivi dans AdWords avec des paramètres [!DNL Marketo Measure] {#how-to-set-up-a-tracking-template-in-adwords-with-marketo-measure-parameters}

N’oubliez pas que vous devez ajouter des modèles de suivi au niveau [!UICONTROL Compte], [!UICONTROL Campagne] ou Groupe d’annonces dans AdWords. Si vous ajoutez des modèles de suivi au niveau Mot-clé, Lien de site ou Annonce, votre annonce devra passer par le processus de révision et d&#39;approbation et vous risquez de redémarrer l&#39;historique de performances de vos annonces. En savoir plus sur la [création de modèles de suivi](https://support.google.com/adwords/answer/6076199?hl=en#tracking){target="_blank"}.

1. Connectez-vous à votre compte [!DNL Google AdWords].
1. Accédez à la vue [!UICONTROL Campagnes] depuis la barre de navigation de gauche.
1. Accédez à &quot;[!UICONTROL Settings]&quot;, également dans la barre de navigation de gauche.
1. Basculer vers la vue &quot;[!UICONTROL Paramètres du compte]&quot; en haut
1. Développez la section &quot;[!UICONTROL Tracking]&quot;
1. Collez l’une des chaînes de texte suivantes dans le modèle de suivi pour définir la valeur du modèle :

   * Si vous avez des points d’interrogation dans TOUTES vos URL, utilisez le texte d’URL suivant :

   `{lpurl}&_bt={creative}&_bk={keyword}&_bm={matchtype}&_bn={network}&_bg={adgroupid}`

   * Si vous ne disposez d’aucun point d’interrogation sur l’une de vos URL, ajoutez le texte URL suivant :

   `{lpurl}?_bt={creative}&_bk={keyword}&_bm={matchtype}&_bn={network}&_bg={adgroupid}*`

   Pour éviter que des erreurs ne se produisent lorsque vous balisez manuellement vos URL, il est généralement recommandé de générer automatiquement les paramètres UTM. Cela ne signifie pas nécessairement un balisage automatique avec les paramètres AdWords ou [!DNL Marketo Measure] . Il existe plusieurs outils qui simplifient le processus en générant automatiquement les paramètres de l’URL en fonction des informations que vous fournissez.

   >[!TIP]
   >
   >Si une erreur s’affiche indiquant que le modèle de suivi n’est pas valide, essayez d’effacer le cache de votre navigateur et réessayez, ce qui résout souvent le problème.

## Comment générer automatiquement des balises UTM pour [!DNL Google AdWords] {#how-to-automatically-generate-utm-tags-for-google-adwords}

Les balises UTM peuvent sembler difficiles à créer au début, mais de nombreux outils sont disponibles pour créer facilement des URL avec des paramètres UTM. Vous pouvez utiliser l’une des ressources suivantes ou rechercher d’autres outils sur le Web. Gardez à l’esprit que [!DNL Marketo Measure] n’approuve ou ne garantit rien avec ces plateformes et outils.

**[!DNL Google URL]Builder**

Google URL Builder est un outil standard permettant de créer des URL correctement formatées à l’aide de balises UTM. Saisissez l’URL et la valeur souhaitée de chaque paramètre, puis cliquez sur &quot;[!UICONTROL Generate URL]&quot;. Il s’agit d’un outil idéal à utiliser si vous avez seulement quelques URL à baliser. Accédez à l’outil [ici](https://support.google.com/analytics/answer/1033867?hl=fr){target="_blank"}.

**Feuille de calcul Google générée par EpikOne**

Cette feuille de calcul comporte une formule qui génère automatiquement des URL de destination balisées. Il s’agit d’un outil idéal à utiliser si un grand nombre de liens doivent être balisés. Accédez à la feuille de calcul [ici](https://spreadsheets.google.com/ccc?key=p7c_HKcmspSUfEYSO0gskKw&hl=en){target="_blank"}.

**Outil de balisage de lien Rafflecopter**

La feuille de calcul créée par Rafflecopter est une version modifiée de la feuille de calcul [!DNL EpikOne's]. Elle contient également une formule qui génère automatiquement des liens de destination balisés que vous pouvez utiliser.

Chacun de ces outils comporte des instructions détaillées sur l’utilisation et la modification en fonction de vos besoins. L’outil est disponible [ici](https://docs.google.com/spreadsheets/d/1QCIr1WUJQHE68cA4VTks2XE7nxuryaUymCEy_23-Oew/edit#gid=0){target="_blank"}.

**Effin Amazing UTM Builder**

Cet outil est une extension Chrome qui vous permet de générer rapidement des balises UTM. Trouvez-le [ici](https://chrome.google.com/webstore/detail/effin-amazing-utm-builder/eoaapiimcaimddnfhfnifgkinmpcbccp?hl=en){target="_blank"}.

## Publicités Bing {#bing-ads}

Bing Ads est une plateforme intégrée qui vous permet d’activer le balisage automatique pour les URL ou d’utiliser un outil tiers, tel que [!DNL Marketo Measure], pour baliser les publicités. [!DNL Bing Ads] repose également sur les paramètres UTM.

Notre intégration prend en charge les types d’annonces suivants :

* Publicité textuelle
* Publicité mobile
* Annonce textuelle développée


La fonction de balisage automatique de Bing Ads ajoute les paramètres UTM suivants :

* Utm_source
* Utm_medium
* Utm_term

Le balisage automatique de Bing Ads ajoute également le paramètre personnalisé suivant :

`_bt={adid}`

La chaîne se présente comme suit :

`{lpurl}?_bt={adid}&utm_term={keyword}&utm_source=Bing_Yahoo&utm_medium=CPC`

Il est important de noter que [!DNL Bing Ads] vous permet d’ajouter encore plus de paramètres en utilisant leurs balises personnalisées dans vos URL finales pour obtenir plus de granularité, si vous le souhaitez.

Un modèle de suivi peut être utilisé si vous le souhaitez, mais il n’est pas nécessaire que [!DNL Bing Ads] et [!DNL Marketo Measure] s’intègrent. En effet, [!DNL Bing] permet de modifier les publicités sans modifier l’historique. [!DNL Marketo Measure] peut donc mettre à jour l’URL de destination.

Le balisage automatique doit être activé via [!DNL Marketo Measure] afin que les paramètres personnalisés [!DNL Marketo Measure] puissent être automatiquement ajoutés. Il n’y a aucun risque de perdre l’historique des performances publicitaires antérieures avec Bing Ads.

Pour plus d’informations sur l’ajout de balises sur leur plateforme, rendez-vous sur le site web [[!DNL Bing Ads]](https://advertise.bingads.microsoft.com/en-us/blog/post/august-2016/upgraded-urls-now-available-in-bing-ads-an-easier-way-to-manage-your-tracking-urls){target="_blank"}.

## Publicités Facebook {#facebook-ads}

L&#39;intégration [!DNL Marketo Measure] à [!DNL Facebook] lui permet de télécharger automatiquement les informations publicitaires et de baliser l&#39;URL avec ses paramètres. [!DNL Marketo Measure] va extraire les informations sur les campagnes et les jeux de publicités par le biais de notre balisage automatique. La visionneuse de publicités renseigne le champ Nom du groupe publicitaire . Pour plus d&#39;informations sur la configuration des balises URL sur la plateforme [!DNL Facebook], consultez la page [!DNL Facebook] [business](https://www.facebook.com/business/help/1016122818401732/?ref=u2u){target="_blank"} .

Avant d’activer le balisage automatique avec [!DNL Facebook Ads], il est important d’exporter l’historique des performances précédent au format CSV. À ce stade, lorsque [!DNL Marketo Measure] balises [!DNL Facebook Ads] avec son paramètre _bf, [!DNL Facebook] lit les publicités comme neuves et efface l’historique des performances. Par conséquent, il est important d’exporter un enregistrement des performances précédentes si cela vous intéresse, ainsi qu’à votre entreprise.

Notez que vous pouvez connecter votre compte [!DNL Facebook] à tout moment à l’application [!DNL Marketo Measure] et qu’aucune donnée ne sera perdue ; c’est seulement lorsque le balisage automatique est activé que l’historique des performances est effacé.

Pour plus d’informations sur l’exportation de [!DNL Facebook] rapports d’annonce, voir [cet article](https://www.facebook.com/business/help/393890194130036){target="_blank"} depuis Facebook.

## Contenu sponsorisé linkedIn {#linkedin-sponsored-content}

L’intégration de LinkedIn permet à [!DNL Marketo Measure] de baliser les URL de destination sur le contenu sponsorisé [!DNL LinkedIn], ce qui permet finalement à [!DNL Marketo Measure] de suivre un utilisateur à travers tout son parcours de point de contact et de mapper l’activité à la campagne et à la création spécifiques [!DNL LinkedIn]. Cela fournit aux clients des informations sur le retour sur investissement de leur activité [!DNL LinkedIn]. [!DNL Marketo Measure] recherche des créatifs avec un partage [!DNL LinkedIn] unique et ajoute un paramètre `?_bl={creativeId}` à la fin.

Comme [!DNL LinkedIn] les partages peuvent être utilisés sur plusieurs campagnes et créatifs, nous demandons aux clients de ne pas copier/cloner/dupliquer les créatifs existants afin qu’ils puissent conserver leur unicité. Si des partages sont détectés et ne sont utilisés que sur un seul élément créatif, [!DNL Marketo Measure] peut baliser le partage en l’état sans avoir à recréer aucun élément créatif ou partage, et l’historique de toutes les publicités (impressions, clics, partages) reste inchangé.

Dès qu’un partage est trouvé pour être partagé sur plusieurs créatifs, [!DNL Marketo Measure] devra passer par un processus de mise en pause, de copie et de rebalisage pour créer un ensemble unique. [!DNL Marketo Measure] interrompt et archive les créatifs en direct, ce qui signifie que les créatifs contenant les impressions, les clics et les partages sur les réseaux sociaux sont également archivés.

## Plateformes non intégrées {#non-integrated-platforms}

Pour les plateformes qui ne sont pas intégrées à [!DNL Marketo Measure], la fonctionnalité de balisage automatique [!DNL Marketo Measure] ne peut pas être utilisée. Les paramètres doivent être ajoutés manuellement.
