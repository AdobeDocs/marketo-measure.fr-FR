---
unique-page-id: 18874594
description: Plateformes d’annonces intégrées [!DNL Marketo Measure] - Documentation du produit
title: Plateformes d’annonces intégrées
exl-id: df30ee8a-8b07-4f14-94e8-cc482fca8b18
source-git-commit: b59c79236d3e324e8c8b07c5a6d68bd8176fc8a9
workflow-type: tm+mt
source-wordcount: '1749'
ht-degree: 0%

---

# Plateformes d’annonces intégrées {#integrated-ad-platforms}

[!DNL Marketo Measure] dispose de connexions API avec Google AdWords, Microsoft BingAds, [!DNL Facebook] Publicités et Gestionnaire de campagnes DoubleClick. Grâce à ces connexions API, [!DNL Marketo Measure] peut facilement extraire des données et les transmettre à votre gestion de la relation client avec l’application externe Buyer. Aucun chargement manuel des coûts ou des données n’est requis. Il vous suffit simplement de connecter vos comptes et de les autoriser au [!DNL Marketo Measure] application. [!DNL Marketo Measure] téléchargera alors automatiquement vos coûts marketing à partir des plateformes et les chargera dans la variable [!DNL Marketo Measure] application. Si vous choisissez d’activer le balisage automatique pour AdWords, BingAds ou [!DNL Facebook] Publicités, [!DNL Marketo Measure] ajoute automatiquement ses paramètres aux URL de vos publicités.

## Comment connecter des plateformes d’annonces publicitaires {#how-to-connect-ad-platforms}

Avant d&#39;entrer dans les détails de chaque plateforme, nous allons passer en revue la manière de connecter n&#39;importe lequel de ces comptes à [!DNL Marketo Measure]. Première connexion à [!DNL Marketo Measure] et accédez à la **[!UICONTROL Paramètres]** sous l’option **[!UICONTROL Mon compte]** dans la partie supérieure gauche de l’écran. Ensuite, sélectionnez **[!UICONTROL Connexions]** sous le **[!UICONTROL Intégrations]** sur la gauche.

Comme illustré dans l’image ci-dessous, un bouton s’affiche pour configurer de nouvelles connexions d’annonces.

![](assets/2.png)

Après avoir cliqué sur [!UICONTROL Configurer une nouvelle connexion aux publicités] , une fenêtre (illustrée ci-dessous) s’affiche avec quatre publicités. [!UICONTROL connect]types d’ions. Cliquez sur Se connecter et une autre fenêtre s’affiche pour vous demander des informations d’identification. Saisissez les informations d’identification, puis cliquez sur [!UICONTROL autoriser] pour connecter le compte à [!DNL Marketo Measure].

![](assets/select-account-type.png)

## Google AdWords {#google-adwords}

Lorsque vous créez vos publicités dans [!DNL Google AdWords], vous êtes invité à baliser vos campagnes de l’une des trois manières suivantes : balisage manuel, balisage automatique ou création d’un modèle de suivi. Le balisage manuel de l’URL d’AdWords repose sur la définition et l’ajout des paramètres à la fin des URL des publicités. Le balisage manuel permet à toute plateforme non Google de lire facilement les données collectées par les paramètres.

Le modèle de suivi est un outil fourni par Google pour ajouter ce qu’il appelle des paramètres ValueTrack. Ils fonctionnent de la même manière que les UTM et d’autres paramètres de balisage.

## Que se passe-t-il lorsque le balisage automatique est activé {#what-happens-when-auto-tagging-is-enabled}

[!DNL Marketo Measure] Recherches de modèles de suivi dans vos [!DNL AdWords] compte :

* *Option A*: Modèle de suivi trouvé. [!DNL Marketo Measure] ajoute ses paramètres au modèle.
* *Option B*: La redirection tierce est disponible. Si une redirection tierce est trouvée dans le modèle de suivi, [!DNL Marketo Measure] ne peut pas prendre aucune action. Vous devez ajouter manuellement la variable [!DNL Marketo Measure] balises vers le système tiers. Un exemple de redirection tierce serait un outil de gestion des offres comme Kenshoo ou Marin. En savoir plus sur la manière dont [les outils de gestion des offres ; [!DNL Marketo Measure]](/help/api-connections/utilizing-marketo-measures-api-connections/how-bid-management-tools-affect-marketo-measure.md){target=&quot;_blank&quot;}.

* *Option C*: Aucun modèle de suivi n’a été trouvé. [!DNL Marketo Measure] analysera toutes vos URL de destination de l’annonce pour la variable [!DNL Marketo Measure] paramètres. Selon l’analyse, si :
   * Les paramètres sont détectés : la configuration est terminée !
   * Paramètres introuvables : [!DNL Marketo Measure] ajoute ses paramètres à la fin des URL de destination de l’annonce. [!DNL Marketo Measure] ajoute de nouvelles publicités dans les deux heures qui suivent leur création. Gardez à l’esprit que les paramètres ne seront pas ajoutés à un modèle.

En savoir plus sur notre [[!DNL AdWords] fonctionnalité de balisage automatique](/help/api-connections/utilizing-marketo-measures-api-connections/understanding-marketo-measure-adwords-tagging.md){target=&quot;_blank&quot;}.

## Comment activer [!DNL Marketo Measure] Balisage automatique pour les mots-clés {#how-to-enable-marketo-measure-auto-tagging-for-adwords}

Avant l’activation [!DNL Marketo Measure] balisage automatique, **assurez-vous qu’un modèle de suivi est activé au niveau du compte, de la campagne ou du groupe publicitaire dans votre compte AdWords. Cela est nécessaire pour tout compte Adwords qui aura [!DNL Marketo Measure] le balisage automatique est activé.** L’activation d’un modèle de suivi évite toute perte dans les données de l’historique des performances publicitaires. Notez que l’activation des modèles de suivi au niveau du mot-clé, du lien de site ou de la publicité entraîne le processus de révision et d’approbation de la publicité et peut potentiellement redémarrer l’historique des performances de vos publicités. Si aucun modèle de suivi n’est activé, [!DNL Marketo Measure] ajoute le [!DNL Marketo Measure] les paramètres de suivi directement à l’&quot;URL finale&quot; de l’annonce, ce qui peut également entraîner la perte des données d’historique des publicités.

Une fois que vous avez mis en place un modèle de suivi, veuillez suivre les instructions ci-dessous pour activer [!DNL Marketo Measure] Balisage automatique. Remarque : [!DNL Marketo Measure] balise également automatiquement toute publicité suspendue dans votre compte.

1. Connectez-vous à [!DNL Marketo Measure] compte à l’adresse [experience.adobe.com/marketo-measure](https://experience.adobe.com/marketo-measure){target=&quot;_blank&quot;}.

1. Accédez à [!UICONTROL Mon compte] > [!UICONTROL Paramètres] > [!UICONTROL Intégrations] > [!UICONTROL Connexions].

   ![](assets/4.png)

1. Cliquez sur l’icône en forme de crayon en regard du compte Adwords qui sera [!DNL Marketo Measure] le balisage automatique est activé.

   ![](assets/5.png)

1. Dans le coin supérieur droit, faites basculer le **[!UICONTROL Authentification]** passer à **[!UICONTROL Oui]**. Au bas de la page, cliquez sur **[!UICONTROL En savoir plus]** pour développer la zone de texte, puis cliquez sur **[!UICONTROL Enregistrer]**. La configuration du balisage automatique est terminée.

   ![](assets/6.png)

## Comment configurer un modèle de suivi dans AdWords avec [!DNL Marketo Measure] Paramètres {#how-to-set-up-a-tracking-template-in-adwords-with-marketo-measure-parameters}

Gardez à l’esprit que vous devez ajouter des modèles de suivi à l’adresse [!UICONTROL Compte], [!UICONTROL Campagne] ou au niveau du groupe publicitaire dans AdWords. Si vous ajoutez des modèles de suivi au niveau Mot-clé, Lien de site ou Annonce, votre annonce devra passer par le processus de révision et d&#39;approbation et vous risquez de redémarrer l&#39;historique de performances de vos annonces. En savoir plus sur [création de modèles de tracking](https://support.google.com/adwords/answer/6076199?hl=en#tracking){target=&quot;_blank&quot;}.

1. Connectez-vous à votre [!DNL Google AdWords] Compte.
1. Accédez à [!UICONTROL Campagnes] vue depuis la barre de navigation de gauche
1. Accédez à &quot;[!UICONTROL Paramètres]&quot;, également dans la barre de navigation de gauche
1. Basculez vers le[!UICONTROL Paramètres du compte]&quot; vue supérieure
1. Développez le[!UICONTROL Tracking]section &quot;
1. Collez l’une des chaînes de texte suivantes dans le modèle de suivi pour définir la valeur du modèle :

   * Si vous avez des points d’interrogation dans TOUTES vos URL, utilisez le texte d’URL suivant :

   `{lpurl}&_bt={creative}&_bk={keyword}&_bm={matchtype}&_bn={network}&_bg={adgroupid}`

   * Si vous ne disposez d’aucun point d’interrogation sur l’une de vos URL, ajoutez le texte d’URL suivant :

   `{lpurl}?_bt={creative}&_bk={keyword}&_bm={matchtype}&_bn={network}&_bg={adgroupid}*`

   Pour éviter que des erreurs ne se produisent lorsque vous balisez manuellement vos URL, il est généralement recommandé de générer automatiquement les paramètres UTM. Cela ne signifie pas nécessairement un balisage automatique avec AdWords ou [!DNL Marketo Measure] , il existe plusieurs outils qui simplifient le processus en générant automatiquement les paramètres de l’URL en fonction des informations que vous fournissez.

   >[!TIP]
   >
   >Si une erreur s’affiche indiquant que le modèle de suivi n’est pas valide, essayez d’effacer le cache de votre navigateur et réessayez, ce qui résout souvent le problème.

## Comment générer automatiquement des balises UTM pour [!DNL Google AdWords] {#how-to-automatically-generate-utm-tags-for-google-adwords}

Les balises UTM peuvent sembler difficiles à créer au début, mais de nombreux outils sont disponibles pour créer facilement des URL avec des paramètres UTM. Vous pouvez utiliser l’une des ressources suivantes ou rechercher d’autres outils sur le Web. Gardez à l’esprit que : [!DNL Marketo Measure] n’approuve ni ne garantit quoi que ce soit avec ces plateformes et outils.

**[!DNL Google URL]Créateur**

Google URL Builder est un outil standard permettant de créer des URL correctement formatées à l’aide de balises UTM. Il vous suffit de saisir l’URL et la valeur souhaitée de chaque paramètre et de cliquer sur &quot;[!UICONTROL Générer l’URL]&quot;. Il s’agit d’un outil idéal à utiliser si vous ne disposez que d’une poignée d’URL à baliser. Accès à l’outil [here](https://support.google.com/analytics/answer/1033867?hl=en){target=&quot;_blank&quot;}.

**Feuille de calcul Google générée par EpikOne**

Cette feuille de calcul comporte une formule qui génère automatiquement des URL de destination balisées. Il s’agit d’un outil idéal à utiliser si un grand nombre de liens doivent être balisés. Accès à la feuille de calcul [here](https://spreadsheets.google.com/ccc?key=p7c_HKcmspSUfEYSO0gskKw&amp;hl=en){target=&quot;_blank&quot;}.

**Outil de balisage de lien de l’outil Rafflecopter**

La feuille de calcul créée par Rafflecopter est une version modifiée de [!DNL EpikOne's] feuille de calcul. Elle contient également une formule qui génère automatiquement des liens de destination balisés que vous pouvez utiliser.

Chacun de ces outils comporte des instructions détaillées sur l’utilisation et la modification en fonction de vos besoins. L’outil est disponible [here](https://docs.google.com/spreadsheets/d/1QCIr1WUJQHE68cA4VTks2XE7nxuryaUymCEy_23-Oew/edit#gid=0){target=&quot;_blank&quot;}.

**Effet impressionnant UTM Builder**

Cet outil est une extension Chrome qui vous permet de générer rapidement des balises UTM. Trouvez-le [here](https://chrome.google.com/webstore/detail/effin-amazing-utm-builder/eoaapiimcaimddnfhfnifgkinmpcbccp?hl=en){target=&quot;_blank&quot;}.

## Publicités Bing {#bing-ads}

Bing Ads est une plateforme intégrée qui vous permet d’activer le balisage automatique pour les URL ou d’utiliser un outil tiers, tel que [!DNL Marketo Measure], pour baliser des publicités. [!DNL Bing Ads] repose également sur les paramètres UTM.

La fonction de balisage automatique de Bing Ads ajoute les paramètres UTM suivants :

* Utm_source
* Utm_medium
* Utm_term

Le balisage automatique de Bing Ads ajoute également le paramètre personnalisé suivant :

`_bt={adid}`

La chaîne se présente comme suit :

`{lpurl}?_bt={adid}&utm_term={keyword}&utm_source=Bing_Yahoo&utm_medium=CPC`

Il est important de noter que [!DNL Bing Ads] vous permet d’ajouter encore plus de paramètres en utilisant leurs balises personnalisées dans vos URL finales pour obtenir plus de granularité, si vous le souhaitez.

Un modèle de suivi peut être utilisé si nécessaire, mais il n’est pas nécessaire pour [!DNL Bing Ads] et [!DNL Marketo Measure] pour intégrer . Ceci est dû au fait que [!DNL Bing] permet de modifier les publicités sans modifier l’historique. [!DNL Marketo Measure] peut mettre à jour l’URL de destination.

Le balisage automatique doit être activé via [!DNL Marketo Measure] pour que la variable [!DNL Marketo Measure] peuvent être automatiquement ajoutés. Il n’y a aucun risque de perdre l’historique des performances publicitaires antérieures avec Bing Ads.

Visitez le [[!DNL Bing Ads]](https://advertise.bingads.microsoft.com/en-us/blog/post/august-2016/upgraded-urls-now-available-in-bing-ads-an-easier-way-to-manage-your-tracking-urls)Site web {target=&quot;_blank&quot;} pour plus d’informations sur l’ajout de balises sur leur plateforme.

## Publicités Facebook {#facebook-ads}

Le [!DNL Marketo Measure] intégration avec [!DNL Facebook] permet de télécharger automatiquement les informations publicitaires et de baliser l’URL avec ses paramètres. [!DNL Marketo Measure] extrait les informations sur la campagne et la visionneuse de publicités par le biais de notre balisage automatique. La visionneuse de publicités renseigne le champ Nom du groupe publicitaire . Pour plus d’informations sur la configuration des balises d’URL sur la page [!DNL Facebook] platform, rendez-vous sur la page [!DNL Facebook] [commerce](https://www.facebook.com/business/help/1016122818401732/?ref=u2u)Page {target=&quot;_blank&quot;}.

Avant d’activer le balisage automatique avec [!DNL Facebook Ads], il est important d’exporter l’historique des performances précédent au format CSV. À ce stade, lorsque [!DNL Marketo Measure] tags [!DNL Facebook Ads] avec son paramètre _bf, [!DNL Facebook] lit les publicités comme étant toutes nouvelles et efface l’historique des performances. Par conséquent, il est important d’exporter un enregistrement des performances précédentes si cela vous intéresse, ainsi qu’à votre entreprise.

Veuillez noter que vous pouvez connecter votre [!DNL Facebook] à tout moment au [!DNL Marketo Measure] et qu’aucune donnée ne sera perdue ; c’est seulement lorsque le balisage automatique est activé que l’historique des performances est effacé.

[Consultez cet article](https://www.facebook.com/business/help/393890194130036){target=&quot;_blank&quot;} à partir de Facebook pour plus d’informations sur l’exportation [!DNL Facebook] Rapports publicitaires.

## Contenu sponsorisé linkedIn {#linkedin-sponsored-content}

L’intégration LinkedIn permet [!DNL Marketo Measure] pour baliser les URL de destination sur [!DNL LinkedIn] Contenu sponsorisé, qui permet finalement [!DNL Marketo Measure] pour suivre un utilisateur tout au long de son parcours de point de contact et mapper l’activité à [!DNL LinkedIn] Campaign et Creative. Cela fournit aux clients des informations sur le retour sur investissement de leur [!DNL LinkedIn] activité. [!DNL Marketo Measure] recherche des créatifs avec un [!DNL LinkedIn] Partager et ajouter une `?_bl={creativeId}` à la fin.

Parce que [!DNL LinkedIn] Les partages peuvent être utilisés sur plusieurs campagnes et créatifs. Nous demandons aux clients de ne pas copier/cloner/dupliquer des créatifs existants afin de conserver leur unicité. Si des partages sont détectés et ne sont utilisés que sur un seul élément créatif, [!DNL Marketo Measure] Vous pouvez baliser le partage en l’état sans avoir à recréer de Creative ou de Partages, et l’historique de toutes les publicités (impressions, clics, partages) restera inchangé.

Dès qu’un partage est trouvé partagé entre plusieurs créatifs, [!DNL Marketo Measure] doit passer par un processus de mise en pause, de copie et de rebalisage pour créer un ensemble unique. [!DNL Marketo Measure] interrompt et archiver les créatifs en direct, ce qui signifie que les créatifs contenant les impressions, les clics et les partages sur les réseaux sociaux sont également archivés.

## Plateformes non intégrées {#non-integrated-platforms}

Pour les plateformes qui ne sont pas intégrées à [!DNL Marketo Measure], la variable [!DNL Marketo Measure] la fonctionnalité de balisage automatique ne peut pas être utilisée. Les paramètres doivent être ajoutés manuellement.
