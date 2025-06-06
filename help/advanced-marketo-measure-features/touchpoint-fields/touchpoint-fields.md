---
unique-page-id: 37355835
description: Champs de point de contact - [!DNL Marketo Measure]
title: Champs de point de contact
exl-id: d6c2bd60-5341-4a52-939a-942afc093306
feature: Touchpoints
source-git-commit: 3424f8a63da40f8762defae1e6ae22ebe60530d0
workflow-type: tm+mt
source-wordcount: '1960'
ht-degree: 0%

---

# Champs de point de contact {#touchpoint-fields}

Historiquement, lorsque les clients sont embarqués avec [!DNL Marketo Measure] et que nous n’avons pas d’intégration de balisage direct, notre équipe du service client éduque nos clients sur la manière de baliser correctement leurs landing pages afin qu’ils utilisent le format UTM approprié et que nous puissions résoudre leurs publicités. Certains de ces clients n’utilisent pas les UTM, mais utilisent plutôt leurs propres paramètres de balisage, ce qui signifie qu’il peut s’avérer très long de modifier toutes leurs landing pages sur tous leurs réseaux publicitaires avec une nouvelle structure de balisage imposée par [!DNL Marketo Measure]. Afin de s’adapter à leur structure de balisage, nous acceptons désormais des paramètres personnalisés qui peuvent être mappés avec nos définitions de règles. L’objectif est de s’adapter à l’utilisation par les clients de leurs paramètres de suivi personnalisés afin que nous n’ayons pas à les obliger à modifier leur structure d’URL.

>[!AVAILABILITY]
>
>Disponible avec la segmentation complète dans les abonnements de niveau 2.

>[!NOTE]
>
>Il s’agit d’une fonctionnalité avancée qui ne doit être configurée que par les services professionnels.

## Activation de la fonctionnalité {#enabling-the-feature}

Dans le menu [!DNL Marketo Measure] Paramètres, accédez à la page Champs de point de contact . De là, vous pouvez activer la fonction en sélectionnant **Oui** sous **Activer les champs calculés**. Une fois la fonction activée, vous pouvez créer des champs de point de contact.

![](assets/one.png)

## Comment {#how-to}

Pour créer un champ calculé, n’oubliez pas que l’utilisateur peut effectuer trois actions différentes : extraire, mapper et concaténer. Ils sont également appelés opérateurs pour définir un champ calculé.

### Extractions {#extracts}

L’opérateur [!UICONTROL extrait] extrait la valeur d’un champ à partir d’un autre emplacement, tel que : un champ Campagne, un champ de piste ou, dans un cas d’utilisation plus avancé, extraire des paramètres personnalisés de la page d’entrée. Il le place ensuite sur un champ de point de contact.

**Exemple #1**

Il existe un champ personnalisé sur le contact, campaign_source__c, que le client souhaite déposer sur le point de contact à des fins de création de rapports. Vous pouvez définir une règle pour créer un champ calculé appelé &quot;Source de campagne&quot; et y déposer la valeur.

Objectif : utilisez la valeur d’un champ personnalisé et placez-la sur l’objet Point de contact pour faciliter la création de rapports.

* Créez un champ calculé et étiquetez-le &quot;Source Campaign&quot;.
* Définissez la règle en commençant par la recherche du champ Contact.Campaign_Source__c .
* Utilisez l’opérateur &quot;extracts&quot; puisque nous devons extraire la valeur du paramètre .
* Pour extraire la chaîne complète du champ, nous utiliserons l’expression &quot;(.&#42;)&quot;

   * **(** marque le début de l’extraction
   * **)** marque la fin de l’extraction
   * **.&#42;** nous indique que nous extrayons la chaîne complète

![](assets/two.png)

**Exemple #2**

Ce cas pratique courant permet d’extraire des valeurs des paramètres personnalisés d’une chaîne d’URL. Cela s’avère utile si vous utilisez des paramètres autres que les UTM, mais que vous souhaitez analyser les valeurs sur les champs de point de contact.

**Lien :** `https://www.adobe.com/blog/marketing-revenue-reporting-overview?promo=5OFF` ou `https://www.adobe.com/blog/marketing-revenue-reporting-overview?promo=25OFF`.\
**Objectif :** Créez un champ personnalisé appelé &quot;Code remise&quot; et déposez la valeur &quot;5OFF&quot; ou &quot;25OFF&quot;, quelle que soit la valeur transmise.

* Créez un champ calculé et étiquetez-le &quot;Code remise&quot;.
* Définissez la règle en commençant par la recherche du champ Touchpoint.Session.LandingPage .
* Utilisez l’opérateur &quot;extracts&quot; puisque nous devons extraire la valeur du paramètre .
* Pour extraire la valeur de la promotion, nous définirons la valeur &quot;promo=(\w+)&quot;

   * **(** marque le début de l’extraction
   * **)** marque la fin de l’extraction
   * **\w** nous indique que nous extrayons un &quot;mot&quot; qui inclut 0-9
   * **+** va extraire la valeur complète du paramètre sans limite sur les caractères
   * Notez que vous utilisez une barre oblique (forward slash) et non une barre oblique inverse (back slash).

![](assets/three.png)

**Exemple #3**

Essayons un exemple similaire où nous extrayons un code de suivi tel que : `https://www.adobe.com/blog/marketing-revenue-reporting-overview?cid=123456`.

**Objectif :** Créez un champ calculé et étiquetez-le &quot;Adobe Campaign Id&quot; avec la valeur du paramètre cid.

* Créez un champ calculé et étiquetez-le &quot;Adobe Campaign Id&quot;.
* Définissez la règle en commençant par la recherche du champ Touchpoint.Session.LandingPage .
* Utilisez l’opérateur &quot;extracts&quot; puisque nous devons extraire la valeur du paramètre .
* Pour extraire la valeur &quot;123456&quot;, nous définirons la valeur comme &quot;cid=(\d{6})&quot;

   * **(** marque le début de l’extraction
   * **)** marque la fin de l’extraction
   * **\d** nous indique que nous extrayons un &quot;chiffre&quot;
   * **{6}** correspond au nombre de caractères que nous extrayons

![](assets/four.png)

**Exemple #4**

À mesure que vos landing pages deviennent plus complexes et que vous disposez de plusieurs paramètres de suivi, vous devrez peut-être créer plusieurs champs de point de contact et extraire plusieurs valeurs, par exemple :
`https://www.adobe.com/blog/marketing-revenue-reporting-overview?trackID=123456&country=US&campaign_ID=7890`.

**Objectif :** Créez plusieurs champs calculés pour &quot;Pays cible&quot; et &quot;Identifiant de campagne personnalisé&quot; avec les valeurs respectives des paramètres.

* Créez un champ calculé et étiquetez-le &quot;Pays cible&quot;
* Définissez la règle en commençant par la recherche du champ Touchpoint.Session.LandingPage .
* Utilisez l’opérateur &quot;extracts&quot; puisque nous devons extraire la valeur du paramètre .
* Pour extraire la valeur &quot;US&quot;, nous définirons la valeur &quot;country=(\w{2})&quot;

   * **(** marque le début de l’extraction
   * **)** marque la fin de l’extraction
   * **\w** nous indique que nous extrayons un &quot;mot&quot;
   * **{2}** correspond au nombre de caractères que nous extrayons

* Créez un champ calculé et étiquetez-le &quot;Identifiant de campagne personnalisé&quot;.
* Définissez la règle en commençant par la recherche du champ Touchpoint.Session.LandingPage .
* Utilisez l’opérateur &quot;extracts&quot; puisque nous devons extraire la valeur du paramètre .
* Pour extraire la valeur &quot;123456&quot;, nous définirons la valeur &quot;campaign_ID=(\d{6})&quot;

   * **(** marque le début de l’extraction
   * **)** marque la fin de l’extraction
   * **\d** nous indique que nous extrayons un &quot;chiffre&quot;
   * **{6}** correspond au nombre de caractères que nous extrayons

![](assets/five.png)

### Mappages sur {#maps-to}

L’opérateur [!UICONTROL mappe vers] crée un tableau des valeurs qui doivent être traduites ou regroupées dans une autre valeur. En règle générale, cela prend la forme d’une valeur clé où un code représente un nom convivial et doit être associé à ce nom convivial.

**Exemple #1**

Il existe des campagnes que vous avez créées pour une &quot;promotion de fin d’été&quot; et une &quot;promotion de Black Friday&quot; qui s’exécutent sur plusieurs canaux. Vous souhaitez créer un champ calculé appelé &quot;Initiative&quot; et associer tous les points de contact avec une &quot;promotion de fin d’été&quot; ou une &quot;promotion du vendredi noir&quot; à une valeur d’initiative telle que &quot;Promotions&quot;, en plus d’autres valeurs possibles.

![](assets/six.png)

**Exemple #2**

Maintenant que nous avons appris à extraire et à mapper les champs, combinons ces actions pour extraire d&#39;abord une valeur d&#39;un paramètre, puis associons-la à un nom convivial qui a un peu plus de sens. Commençons par cette landing page : `https://www.adobe.com/blog/marketing-revenue-reporting-overview?BZ=04-01-09-03-10`.

**Objectif :** Créez plusieurs champs calculés, où le premier numéro correspond à une région, le second à un produit, le troisième à une initiative, le quatrième à un personnage et le cinquième à une plateforme multimédia. Associez ensuite la valeur numérique à un nom convivial.

* Créez un champ calculé et étiquetez-le &quot;Région&quot;.
* Définissez la règle en commençant par la recherche du champ Touchpoint.Session.LandingPage .
* Utilisez l’opérateur &quot;[!UICONTROL extracts]&quot; puisque nous devons extraire la valeur du paramètre
* Pour extraire la valeur &quot;04&quot;, nous définirons la valeur comme &quot;BZ=(\d{2})-\d{2}-\d{2}-\d{2}-\d{2}-\d{2}&quot;

   * **(** marque le début de l’extraction

      * Puisque nous extrayons uniquement les 4, seuls les premiers chiffres ont la parenthèse ouverte
   * **)** marque la fin de l’extraction

      * Puisque nous extrayons uniquement les 4, seuls les premiers chiffres comportent des parenthèses fermées
   * **\d** nous indique que nous extrayons un &quot;chiffre&quot;
   * **{2}** correspond au nombre de caractères que nous extrayons



* Cliquez sur [!UICONTROL Enregistrer]. Vous devez enregistrer votre nouveau champ pour pouvoir l’utiliser pour la règle suivante !
* Ensuite, nous allons mapper toutes les valeurs possibles pour les premiers chiffres à ses noms conviviaux.
* Créez un champ calculé et étiquetez-le &quot;Nom_région&quot;.
* Définissez la règle en commençant par la recherche de votre champ extrait. Dans ce cas, [!DNL Touchpoint.Region]
* Utilisez l’opérateur &quot;[!UICONTROL mappe sur &#x200B;]&quot; puisque nous voulons créer un mappage pour chaque nombre sur sa valeur.
* Un tableau vous est présenté pour répertorier chaque mappage. Au final, il ressemblera à ceci :
* En fonction du mappage et de l’URL ci-dessus, la &quot;Region_Value&quot; d’un point de contact avec cette page d’entrée serait &quot;EMEA&quot;.
* Répétez l’extraction et le mappage pour les 4 jeux de chiffres restants.

   * Pour extraire le 01, vous devez définir la valeur comme &quot;BZ=\d{2}-**(\d{2})**-\d{2}-\d{2}-\2\&rbrace;-\d{2}&quot;
   * Pour extraire la valeur 09, vous devez définir la valeur comme &quot;BZ=\d{2}-\d{2}-**(\d{2})**-\d{2}-\d{2}{2}&quot;
   * Pour extraire la valeur 03, vous devez définir la valeur comme &quot;BZ=\d{2}-\d{2}-\d{2}-**(\d{2})**-\d{2}&quot;
   * Pour extraire la valeur 10, vous devez définir la valeur comme &quot;BZ=\d{2}-\d{2}-\d{2}-\d{2}-**(\d{2})**&quot;

![](assets/seven.png)

### Concaténes {#concatenates}

L’opérateur [!UICONTROL concatenates] combine en un seul champ les valeurs de plusieurs champs. Cela s’avère utile pour créer une valeur personnalisée qui extrait des données dans différents champs afin de

**Exemple #1**

Il existe des champs distincts sur l’objet Opportunity pour Segment__c et Note__c que l’utilisateur souhaite combiner en un seul champ sur l’objet Touchpoint à des fins de création de rapports. En concaténant les champs, vous verrez des valeurs telles que Enterprise_A ou Mid-Market_B.

![](assets/eight.png)

## Champs et segments de point de contact {#touchpoint-fields-and-segments}

Maintenant que les valeurs de votre URL ont été analysées et existent sur le point de contact, les nouveaux champs s’affichent partout où les champs de point de contact sont utilisés, comme la création de segments ou la définition de règles de suppression de point de contact.

Cette version de produit offre la possibilité de créer des segments à l’aide des champs de point de contact. Les segments n’ont pas pu être créés antérieurement avec les champs de point de contact.

![](assets/nine.png)

Pour faciliter la création de segments, il est désormais possible de créer des segments dynamiques à partir des champs de point de contact qui ont été créés. Par exemple, si vous avez créé un champ de point de contact qui analyse une région géographique, plutôt que de créer un segment pour chaque région possible, vous pouvez configurer un segment et nous créerons des segments pour chaque instance afin qu’une nouvelle valeur apparaisse. Cela s’avère extrêmement utile si un attribut tel que le code postal doit être analysé et utilisé comme segment !

Votre configuration ressemblerait à la capture d’écran ci-dessous. Le nom du segment extrait dynamiquement la valeur Champ de point de contact à l’aide des accolades pour rechercher votre champ.

![](assets/ten.png)

La règle fait référence au même champ de point de contact et recherche des valeurs &quot;non égales à nulles&quot;.

![](assets/eleven.png)

## Questions fréquentes {#faq}

**Y a-t-il un nombre maximal de champs de point de contact que nous pouvons créer ?**

La limite est de 100 champs.

**Je ne vois pas mon nouveau champ de point de contact que je viens de créer dans la liste de sélection. Où est-il ?**

N’oubliez pas d’enregistrer vos règles après les avoir créées. Si vous ne voyez pas votre nouveau champ, vérifiez si vous avez enregistré. Vous devez enregistrer votre nouveau champ pour pouvoir l’utiliser pour la règle suivante.

>[!NOTE]
>
>En raison du niveau de complexité, un champ de point de contact qui utilise l’opérateur &quot;mappe à&quot; n’est pas disponible pour être utilisé dans un autre champ de point de contact.

**Quelle expression puis-je utiliser pour extraire plusieurs paramètres d’une seule page d’entrée ?**

Comme dans l’exemple d’extraction #4, vous devez créer plusieurs champs pour extraire chacun des paramètres. Ainsi, si vous avez cinq valeurs différentes, vous allez créer cinq champs de point de contact pour extraire chacun d’eux.

**Pourquoi mes nouveaux champs ne sont-ils pas visibles dans le schéma [!DNL Marketo Measure] ?**

Des travaux supplémentaires sont nécessaires pour exposer les nouveaux champs dans le schéma de Data Warehouse [!DNL Marketo Measure]. Actuellement, les champs sont exposés via les paramètres et la configuration afin que vous puissiez utiliser les champs de point de contact pour créer des segments ou créer des règles de suppression de point de contact.

**Comment puis-je valider la validité de mon expression d’extraction et extraire la valeur correcte ?**

Il existe un outil en ligne ([[!DNL https]://regex101.com/](https://regex101.com/){target="_blank"}) que vous pouvez exécuter et tester l’expression. L’expression apparaît en vert si elle est valide ou en rouge si elle n’est pas valide. En outre, la boîte [!UICONTROL explication] en haut à droite est utile et vous indique ce que vous extrayez.

![](assets/twelve.png)

![](assets/thirteen.png)
