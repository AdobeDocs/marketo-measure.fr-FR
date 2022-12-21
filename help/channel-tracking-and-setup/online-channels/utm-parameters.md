---
unique-page-id: 18874606
description: Paramètres UTM - [!DNL Marketo Measure] - Documentation du produit
title: Paramètres UTM
exl-id: 2b20f3c4-1f39-4ac5-bad1-cb1d630d60e9
source-git-commit: 65e7f8bc198ceba2f873ded23c94601080ad0546
workflow-type: tm+mt
source-wordcount: '948'
ht-degree: 0%

---

# Paramètres UTM {#utm-parameters}

Le balisage des URL est un moyen simple et efficace de capturer des données sur vos efforts de marketing numérique. Il s’agit du processus d’ajout de paramètres à la fin des URL qui collectent et enregistrent des données. Les paramètres les plus couramment utilisés sont les modules de suivi d’URL (UTM), qui sont pris en charge par Google. Cinq paramètres UTM principaux sont disponibles : Moyen, Source, Campagne, Contenu et Terme. Ces points sont abordés plus en détail dans la section suivante.

Les paramètres UTM peuvent être ajoutés manuellement aux URL ou ajoutés par le balisage automatique avec certaines plateformes, comme AdWords par exemple. Le balisage automatique automatise le processus d’ajout de paramètres aux URL. Il existe également la possibilité de [Créateurs d’URL](https://ga-dev-tools.appspot.com/campaign-url-builder/){target=&quot;_blank&quot;} pour accélérer manuellement le balisage des URL. Avec un créateur d’URL, il vous suffit de spécifier les valeurs à utiliser pour chaque paramètre ; le créateur formate l’URL pour vous.

## Que sont les paramètres UTM ? {#what-are-utm-parameters}

Pour comprendre le fonctionnement des paramètres UTM, examinons une URL standard sans UTM :

`http://www.adobe.com`

Maintenant, extrayons une URL avec les UTM :

`http://www.adobe.com?utm_medium=socialmedia&utm_source =facebook&utm_campaign=seasonal-sale&utm_content=photo-400x700px`

Comme vous pouvez le voir, le deuxième lien contient beaucoup plus de texte. Les paramètres de la gestion dynamique des balises s’appliquent toujours au domaine de niveau supérieur (.com dans cet exemple) et commencent par un point d’interrogation. Ensuite, l’ordre des paramètres n’a pas d’importance, mais il est conseillé de respecter une convention d’affectation des noms cohérente. Des esperluettes doivent être placées entre chaque paramètre pour séparer chaque UTM. Maintenant, nous pouvons aller plus en détail sur ce que représente chaque paramètre.

En savoir plus sur [bonnes pratiques pour la configuration des paramètres UTM](/help/channel-tracking-and-setup/online-channels/best-practices-for-setting-up-utm-parameters.md).

**utm_medium**

* Medium identifie les véhicules que vous utilisez pour commercialiser votre entreprise.
* Il répond à la question : &quot;Comment vont-ils vous toucher ?&quot;
* Il indique le canal de niveau supérieur.
* Les médias sociaux, le courrier électronique, le référencement organique et le référencement payant sont autant d’exemples de valeurs moyennes potentielles.
* Ce paramètre mappe les données à la variable [!DNL Marketo Measure] Champ &quot;Moyen&quot;.
* _[!DNL Marketo Measure]Bonne pratique :_ N’utilisez pas ce champ pour appeler un sous-canal. Dans le cas contraire, vous risquez d’avoir des difficultés à générer des rapports sur le canal réel. Utilisez-le pour identifier votre véhicule ou canal marketing. Par exemple, si vous souhaitez utiliser l’e-mail pour commercialiser votre produit, le support est l’e-mail.

**utm_source**

* Source identifie le sous-canal qui est la source de votre trafic.
* Il répond à la question : &quot;D&#39;où vient cette personne ?&quot;
* Dans un exemple de média social, la source du trafic est la plateforme de médias sociaux utilisée.
   * Dans cet exemple, [!DNL Facebook] est la valeur source. Twitter et Instagram sont d’autres exemples. Si le support UTM est [!DNL Paid Search], en revanche, la source UTM peut être AdWords ou BingAds.

* Ce paramètre met en correspondance avec la variable [!DNL Marketo Measure] Champ &quot;Source du point de contact&quot; dans SFDC.
* _[!DNL Marketo Measure]Bonne pratique :_ Ce paramètre surveille la source de votre trafic. Il ne peut donc pas l’utiliser pour indiquer le type de publicité, par exemple le reciblage, le parrainage, etc. Il est préférable de l’utiliser pour effectuer le suivi du sous-canal de niveau supérieur. Rappelez-vous, vous répondez à la question &quot;d&#39;où vient mon trafic ?&quot; Vous recherchez le référent. Dans cet exemple, la source UTM est l’emplacement où se trouve votre publicité (et non la page web proprement dite, car elle est automatiquement suivie en dehors des balises). Si vous effectuez le suivi d’une campagne par courrier électronique, le courrier électronique goutte à goutte est la source.

**utm_campaign**

* Campaign permet d’identifier une campagne marketing spécifique.
* Il répond à la question : &quot;Pourquoi viennent-ils vous voir ?&quot;
* Utilisez cette balise pour indiquer le nom de la campagne publicitaire tel qu’il existe dans [!DNL Google AdWords] ou [!DNL BingAds]ou pour indiquer le nom par lequel vous identifiez la campagne en interne. Vous pouvez même utiliser cette balise pour spécifier d’autres informations, telles que la géolocalisation ou le type de réseau publicitaire.
* Ce paramètre met en correspondance avec la variable [!DNL Marketo Measure] &quot;Champ Nom de la campagne publicitaire&quot; dans SFDC.
* _[!DNL Marketo Measure]Bonne pratique_: Pour déterminer les noms de campagne, évitez d’utiliser des signes de ponctuation ou des espaces vides entre les mots, car leur utilisation peut entraîner des erreurs de codage dans le navigateur. Pour de meilleurs résultats, utilisez plutôt des traits de soulignement.

**utm_content**

* Utilisez le paramètre Contenu UTM lorsque vous souhaitez effectuer le suivi de plusieurs éléments marketing existant sur une seule page web. Par exemple, si vous disposez d’un bouton &quot;Demander une démonstration&quot; et d’un bouton &quot;S’inscrire à notre newsletter hebdomadaire&quot;, et que vous souhaitez savoir lequel génère le plus de trafic, nommez chacun d’eux et utilisez une balise de contenu UTM pour en effectuer le suivi. Le nom de chaque élément de &quot;contenu&quot; est la valeur de la balise.
* Ce paramètre met en correspondance avec la variable [!DNL Marketo Measure] Champ &quot;Contenu de la publicité&quot; dans SFDC.
* _[!DNL Marketo Measure]Bonne pratique_: Il s’agit d’une valeur facultative, mais [!DNL Marketo Measure] recommande de l’utiliser. Cette balise est associée au titre de la publicité ou de la publication marketing dont vous souhaitez effectuer le suivi. Si vous utilisez une publicité avec image, veillez à écrire les dimensions de l’image dans son titre.

**utm_term**

* Le terme est similaire au paramètre de contenu UTM. Terme est idéal pour identifier les mots-clés dans les annonces pour les campagnes payantes. Si vous utilisez la fonction de balisage automatique, ceci est fait pour vous. Si vous n’utilisez pas la fonction de balisage automatique de votre plateforme d’annonces publicitaires, veillez à ajouter soigneusement tous les mots-clés dont vous souhaitez effectuer le suivi.
* Ce paramètre met en correspondance avec la variable [!DNL Marketo Measure] Champ &quot;Texte du mot-clé&quot; dans SFDC.
* _[!DNL Marketo Measure]Bonne pratique_: La balise Terme de la gestion dynamique des balises est facultative, mais elle est idéale pour le suivi des mots-clés. Vérifier l’orthographe et éviter d’utiliser des caractères spéciaux. Si plusieurs mots sont nécessaires, essayez d’utiliser des traits de soulignement ou aucun espace.

Chaque paramètre rassemble des informations relatives à la valeur affectée. La valeur de chaque balise vous permet de suivre et de trier toutes vos campagnes numériques et de répondre aux questions suivantes : où, comment et pourquoi ?

Voici un graphique des paramètres de la gestion dynamique des balises. [!DNL Marketo Measure] analyse et le champ de point de contact auquel ils sont liés :

| **Paramètre UTM** | **Correspondant [!DNL Marketo Measure] Champ** |
|---|---|
| utm_medium | Moyen |
| utm_source | Source du Touchpoint |
| utm_campaign | Nom de la campagne publicitaire |
| utm_content | Contenu de la publicité |
| utm_term | Texte du mot-clé |
