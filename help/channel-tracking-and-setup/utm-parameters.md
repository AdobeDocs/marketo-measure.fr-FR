---
description: Paramètres UTM recommandés pour les utilisateurs de Marketo Measure
title: Paramètres UTM
exl-id: 2b20f3c4-1f39-4ac5-bad1-cb1d630d60e9
feature: UTM Parameters
hidefromtoc: 'yes'
product_v2:
  - id: e6fc4016-a972-4f36-8c30-a6a5f82ad0c8
    internal-label: Marketo Measure
feature_v2:
  - id: 3968a9c0-3e19-5a76-a1f0-f5a9a986c53a
    internal-label: UTM Parameters
source-git-commit: 940fee4abd0e09b6bf513b5e7526d3c242bd31c7
workflow-type: tm+mt
source-wordcount: '944'
ht-degree: 92%
---
# Paramètres UTM {#utm-parameters}

Le balisage des URL est un moyen simple et efficace de capturer des données sur vos efforts de marketing digital. Ce processus consiste à ajouter, à la fin des URL, des paramètres qui collectent et enregistrent les données. Les paramètres les plus couramment utilisés sont les modules de suivi d’URL (UTM pour « Urchin Tracking Modules »), qui sont pris en charge par Google. Il y a cinq paramètres UTM principaux : Support, Source, Campagne, Contenu et Terme. Ces points sont abordés plus en détail dans la section suivante.

Les paramètres UTM peuvent être ajoutés manuellement aux URL ou ajoutés par balisage automatique avec certaines plateformes, comme AdWords. Le balisage automatique automatise le processus d’ajout de paramètres aux URL. Il existe également une option [créateurs d’URL](https://ga-dev-tools.web.app/campaign-url-builder/){target="_blank"} pour accélérer le balisage manuel des URL. Avec un générateur d’URL, il vous suffit de spécifier les valeurs à utiliser pour chaque paramètre pour que l’outil formate l’URL à votre place.

## Que sont les paramètres UTM ?&#x200B; {#what-are-utm-parameters}

Pour comprendre le fonctionnement des paramètres UTM, examinons une URL standard sans UTM :

`http://www.adobe.com`

Examinons à présent une URL avec des balises UTM :

`http://www.adobe.com?utm_medium=socialmedia&utm_source =facebook&utm_campaign=seasonal-sale&utm_content=photo-400x700px`

Le deuxième lien contient plus de texte. Les paramètres UTM s’appliquent toujours au domaine de niveau supérieur (.com dans cet exemple) et commencent par un point d’interrogation. Ensuite, l’ordre des paramètres n’a pas d’importance, mais il est conseillé de respecter une convention de nommage cohérente. Pour séparer chaque UTM, vous devez utiliser des esperluettes entre chaque paramètre. Nous pouvons maintenant nous intéresser plus en détail au fonctionnement de chaque paramètre.

Découvrez les [bonnes pratiques relatives à la configuration des paramètres UTM](/help/channel-tracking-and-setup/best-practices-for-setting-up-utm-parameters.md).

**utm_medium**

* Ce paramètre identifie les supports que vous utilisez pour faire connaître votre société.
* Il répond à la question : « Comment vos clients vous trouvent-ils ? ».
* En d’autres termes, il indique le canal de niveau supérieur.
* Les réseaux sociaux, les e-mails, le référencement naturel et le référencement payant sont tous des exemples de valeurs possibles pour le paramètre « Support ».
* Ce paramètre mappe les données au champ « Support » dans [!DNL Marketo Measure].
* _[!DNL Marketo Measure] Bonne pratique :_n’utilisez pas ce champ pour appeler un sous-canal, sinon vous risquez de rencontrer des difficultés pour générer des rapports sur le canal réel. Utilisez-le pour identifier votre support ou canal marketing. Par exemple, si vous souhaitez utiliser l’e-mail pour promouvoir votre produit, le support est l’e-mail.

**utm_source**

* Ce paramètre identifie le sous-canal qui est la source de votre trafic.
* Il répond à la question : « D’où vient cette personne ? ».
* Dans le cas des réseaux sociaux, la source du trafic correspond à la plateforme de réseaux sociaux que vous utilisez.
  * Dans cet exemple, [!DNL Facebook] est la valeur de la source, Twitter et Instagram en sont d’autres exemples. Si le support UTM est [!DNL Paid Search], en revanche, la source peut être AdWords ou Bing Ads.

* Dans SFDC, ce paramètre mappe les données au champ [!DNL Marketo Measure] « Source du point de contact ».
* _[!DNL Marketo Measure] Bonne pratique :_ce paramètre effectue le suivi de la source de votre trafic. Il n’est donc pas approprié de l’utiliser pour indiquer le type d’annonce, par exemple, reciblage, sponsorisé, etc. Il est préférable de l’utiliser pour effectuer le suivi du sous-canal de niveau supérieur. Rappelez-vous que vous répondez à la question « D’où provient mon trafic ? ». Votre objectif est d’identifier le référent. Dans cet exemple, la source UTM est l’endroit où se trouve votre publicité (et non la page web proprement dite, car elle est automatiquement suivie en dehors des balises). Si vous effectuez le suivi d’une campagne par e-mail progressive, alors il s’agit de votre source.

**utm_campaign**

* Ce paramètre permet d’identifier une campagne marketing spécifique.
* Il répond à la question : « Pourquoi viennent-ils vers vous ? ».
* Utilisez cette balise pour identifier le nom de la campagne publicitaire tel que défini dans [!DNL Google AdWords] ou [!DNL BingAds], ou pour indiquer le nom de campagne que vous utilisez en interne. Vous pouvez également utiliser cette balise pour préciser d’autres informations, telles que la géolocalisation ou le type de réseau publicitaire.
* Dans SFDC, ce paramètre mappe les données au champ [!DNL Marketo Measure] « Nom de la campagne publicitaire ».
* Bonne pratique _[!DNL Marketo Measure]_ : pour fixer les noms de campagne, évitez d’utiliser des signes de ponctuation ou des espaces entre les mots, car cela peut entraîner des erreurs de codage dans le navigateur. Pour optimiser les résultats, utilisez plutôt des traits de soulignement.

**utm_content**

* Utilisez ce paramètre UTM lorsque vous souhaitez effectuer le suivi de plusieurs éléments marketing qui coexistent sur une seule page web. Par exemple, si vous disposez d’un bouton « Demander une démonstration » et d’un bouton « S’abonner à notre newsletter hebdomadaire », et que vous souhaitez savoir lequel génère le plus de trafic, nommez chacun d’entre eux et utilisez une balise UTM de contenu pour en effectuer le suivi. Le nom de chaque élément de contenu correspond à la valeur de la balise.
* Dans SFDC, ce paramètre mappe les données au champ [!DNL Marketo Measure] « Contenu publicitaire ».
* Bonne pratique _[!DNL Marketo Measure]_ : cette valeur est facultative, mais [!DNL Marketo Measure] recommande de l’utiliser. Cette balise est associée au titre de la publicité ou de la publication marketing dont vous souhaitez effectuer le suivi. Si vous utilisez une publicité sous forme d’image, veillez à écrire ses dimensions dans son titre.

**utm_term**

* Cette valeur est similaire au paramètre UTM de contenu. Elle permet d’identifier les mots-clés dans les annonces correspondant à des campagnes payantes. Si vous utilisez la fonctionnalité de balisage automatique, cette opération est effectuée à votre place. Si vous ne l’utilisez pas, veillez à ajouter soigneusement tous les mots-clés dont vous souhaitez effectuer le suivi.
* Dans SFDC, ce paramètre mappe les données au champ [!DNL Marketo Measure] « Texte du mot-clé ».
* Bonne pratique _[!DNL Marketo Measure]_ : la balise UTM de terme est facultative, mais elle est idéale pour le suivi des mots-clés. Vérifiez l’orthographe et évitez d’utiliser des caractères spéciaux. Si plusieurs mots sont nécessaires, essayez d’utiliser des traits de soulignement ou n’utilisez pas d’espaces.

Chaque paramètre collecte des informations relatives à la valeur affectée. La valeur de chaque balise vous permet de suivre et de trier toutes vos campagnes digitales, tout en répondant aux questions suivantes : où, comment et pourquoi ?

Voici un tableau des paramètres UTM analysés par [!DNL Marketo Measure] avec le champ de point de contact correspondant :

| **Paramètre UTM** | **Champ [!DNL Marketo Measure] correspondant** |
|---|---|
| utm_medium | Support |
| utm_source | Source du point de contact |
| utm_campaign | Nom de la campagne publicitaire |
| utm_content | Contenu publicitaire |
| utm_term | Texte du mot-clé |
