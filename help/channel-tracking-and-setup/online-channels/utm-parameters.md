---
unique-page-id: 18874606
description: Paramètres UTM - [!DNL Marketo Measure] - Documentation du produit
title: Paramètres UTM
exl-id: 2b20f3c4-1f39-4ac5-bad1-cb1d630d60e9
feature: UTM Parameters
source-git-commit: 8ac315e7c4110d14811e77ef0586bd663ea1f8ab
workflow-type: ht
source-wordcount: '946'
ht-degree: 100%

---

# Paramètres UTM {#utm-parameters}

Le balisage des URL est un moyen simple et efficace de capturer des données sur vos efforts de marketing digital. Ce processus consiste en un ajout de paramètres à la fin des URL dans le but de collecter et d’enregistrer des données. Les paramètres les plus couramment utilisés sont les modules de suivi d’URL (UTM pour « Urchin Tracking Modules »), qui sont pris en charge par Google. Il y a cinq paramètres UTM principaux : Support, Source, Campagne, Contenu et Terme. Ces points sont abordés plus en détail dans la section suivante.

Les paramètres UTM peuvent être ajoutés manuellement aux URL ou ajoutés par balisage automatique avec certaines plateformes, comme AdWords. Dans ce dernier cas, l’ajout de paramètres aux URL est automatisé. Vous pouvez également utiliser des [créateurs d’URL](https://ga-dev-tools.appspot.com/campaign-url-builder/){target="_blank"} pour accélérer le balisage manuel des URL. Avec ces outils, il vous suffit de spécifier les valeurs à utiliser pour chaque paramètre, et l’URL est formatée pour vous.

## Fonctionnement des paramètres UTM {#what-are-utm-parameters}

Pour comprendre le fonctionnement des paramètres UTM, examinons une URL standard sans UTM :

`http://www.adobe.com`

Maintenant, observons une URL avec des UTM :

`http://www.adobe.com?utm_medium=socialmedia&utm_source =facebook&utm_campaign=seasonal-sale&utm_content=photo-400x700px`

Comme vous pouvez le voir, le deuxième lien contient beaucoup plus de texte. Les paramètres UTM s’appliquent toujours au domaine de niveau supérieur (.com dans cet exemple) et commencent par un point d’interrogation. Ensuite, l’ordre des paramètres n’a pas d’importance, mais il est conseillé de respecter une convention de nommage cohérente. Pour séparer chaque UTM, vous devez utiliser des esperluettes. Nous pouvons maintenant nous intéresser plus en détail au fonctionnement de chaque paramètre.

Découvrez les [bonnes pratiques relatives à la configuration des paramètres UTM](/help/channel-tracking-and-setup/online-channels/best-practices-for-setting-up-utm-parameters.md).

**utm_medium**

* Ce paramètre identifie les supports que vous utilisez pour faire connaître votre société.
* Il répond à la question : « Comment vos clients vous trouvent-ils ? ».
* En d’autres termes, il indique le canal de niveau supérieur.
* Les réseaux sociaux, les e-mails, le référencement naturel et le référencement payant sont des exemples de valeurs potentielles.
* Ce paramètre mappe les données au champ « Support » dans [!DNL Marketo Measure].
* Bonne pratique _[!DNL Marketo Measure] :_ n’utilisez pas ce champ pour appeler un sous-canal. Vous risquez d’avoir des difficultés à générer des rapports sur le canal réel. Utilisez-le pour identifier votre support ou canal marketing. Par exemple, si vous souhaitez utiliser des e-mails pour faire connaître votre produit, il s’agit de votre support marketing.

**utm_source**

* Ce paramètre identifie le sous-canal qui est la source de votre trafic.
* Il répond à la question : « D’où vient cette personne ? ».
* Par exemple, la source du trafic peut être un réseau social.
   * Dans cet exemple, [!DNL Facebook] est la valeur de la source, mais il pourrait également s’agir de Twitter ou d’Instagram. Si le support UTM est [!DNL Paid Search], en revanche, la source peut être AdWords ou Bing Ads.

* Dans SFDC, ce paramètre mappe les données au champ [!DNL Marketo Measure] « Source du point de contact ».
* Bonne pratique _[!DNL Marketo Measure] :_ ce paramètre identifie uniquement la source de votre trafic. Il ne peut donc pas indiquer le type d’annonce, par exemple un reciblage, un parrainage, etc. Il est préférable de l’utiliser pour effectuer le suivi du sous-canal de niveau supérieur. Rappelez-vous, la question posée est « D’où vient mon trafic ? ». Votre objectif est d’identifier le référent. Dans cet exemple, la source UTM est l’endroit où se trouve votre publicité (et non la page web proprement dite, car elle est automatiquement suivie en dehors des balises). Si vous effectuez le suivi d’une campagne par e-mail progressive, alors il s’agit de votre source.

**utm_campaign**

* Ce paramètre permet d’identifier une campagne marketing spécifique.
* Il répond à la question : « Pourquoi vos clients viennent-ils vers vous ? ».
* Utilisez cette balise pour identifier le nom de la campagne publicitaire tel que défini dans [!DNL Google AdWords] ou [!DNL BingAds], ou pour indiquer le nom de campagne que vous utilisez en interne. Vous pouvez même utiliser cette balise pour indiquer d’autres informations, telles que la géolocalisation ou le type de réseau publicitaire.
* Dans SFDC, ce paramètre mappe les données au champ [!DNL Marketo Measure] « Nom de la campagne publicitaire ».
* Bonne pratique _[!DNL Marketo Measure]_ : pour fixer les noms de campagne, évitez d’utiliser des signes de ponctuation ou des espaces entre les mots, car cela peut entraîner des erreurs de codage dans le navigateur. Pour optimiser les résultats, utilisez plutôt des traits de soulignement.

**utm_content**

* Utilisez ce paramètre UTM lorsque vous souhaitez effectuer le suivi de plusieurs éléments marketing qui coexistent sur une seule page web. Par exemple, si vous disposez d’un bouton « Demander une démonstration » et d’un bouton « S’abonner à notre newsletter hebdomadaire », et que vous souhaitez savoir lequel génère le plus de trafic, nommez chacun d’entre eux et utilisez une balise UTM de contenu pour en effectuer le suivi. Le nom de chaque élément de contenu correspond à la valeur de la balise.
* Dans SFDC, ce paramètre mappe les données au champ [!DNL Marketo Measure] « Contenu publicitaire ».
* Bonne pratique _[!DNL Marketo Measure]_ : cette valeur est facultative, mais [!DNL Marketo Measure] recommande de l’utiliser. Cette balise est associée au titre de la publicité ou de la publication marketing dont vous souhaitez effectuer le suivi. Si vous utilisez une publicité sous forme d’image, veillez à écrire ses dimensions dans son titre.

**utm_term**

* Cette valeur est similaire au paramètre UTM de contenu. Elle permet d’identifier les mots-clés dans les annonces correspondant à des campagnes payantes. Si vous utilisez un système de balisage automatique, alors cette fonctionnalité est faite pour vous. Dans le cas contraire, veillez à ajouter soigneusement tous les mots-clés dont vous souhaitez effectuer le suivi.
* Dans SFDC, ce paramètre mappe les données au champ [!DNL Marketo Measure] « Texte du mot-clé ».
* Bonne pratique _[!DNL Marketo Measure]_ : la balise UTM de terme est facultative, mais elle est idéale pour le suivi des mots-clés. Vérifiez l’orthographe et évitez d’utiliser des caractères spéciaux. Si plusieurs mots sont nécessaires, essayez d’utiliser des traits de soulignement ou n’utilisez pas d’espaces.

Chaque paramètre collecte des informations relatives à la valeur affectée. La valeur de chaque balise vous permet de suivre et d’organiser toutes vos campagnes digitales en répondant aux questions suivantes : où, comment et pourquoi ?

Voici un tableau des paramètres UTM analysés par [!DNL Marketo Measure] avec le champ de point de contact correspondant :

| **Paramètre UTM** | **Champ [!DNL Marketo Measure] correspondant** |
|---|---|
| utm_medium | Support |
| utm_source | Source du point de contact |
| utm_campaign | Nom de la campagne publicitaire |
| utm_content | Contenu publicitaire |
| utm_term | Texte du mot-clé |
