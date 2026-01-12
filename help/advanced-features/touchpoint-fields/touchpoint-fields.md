---
description: Champs de point de contact - [!DNL Marketo Measure]
title: Champs de point de contact
exl-id: d6c2bd60-5341-4a52-939a-942afc093306
feature: Touchpoints
source-git-commit: c6090ce0c3ac60cd68b1057c369ce0b3b20aeeee
workflow-type: tm+mt
source-wordcount: '2077'
ht-degree: 0%

---


# Champs de point de contact {#touchpoint-fields}

Historiquement, lorsque les clients rejoignent [!DNL Marketo Measure] et dans le cas où nous n’avons pas d’intégration de balisage directe, notre équipe du succès client informe nos clients sur la manière de baliser correctement leurs pages de destination afin qu’ils utilisent le format UTM approprié et que nous puissions résoudre leurs annonces. Certains de ces clients n’utilisent pas d’UTM, mais utilisent plutôt leurs propres paramètres de balisage. Cela signifie que la modification de toutes leurs pages de destination sur tous leurs réseaux publicitaires peut prendre beaucoup de temps, avec une nouvelle structure de balisage que [!DNL Marketo Measure] applique. Afin de s’adapter à leur structure de balisage, nous acceptons désormais des paramètres personnalisés qui peuvent être mappés à nos définitions de règle. L’objectif est de s’adapter à l’utilisation par les clients de leurs paramètres de tracking personnalisés afin que nous n’ayons pas à les obliger à modifier leur structure d’URL.

>[!AVAILABILITY]
>Disponible maintenant avec la segmentation complète dans les niveaux 2 et 3.
>
>Disponible avec segmentation complète dans les abonnements de niveau 2.

>[!NOTE]
>Il s’agit d’une fonctionnalité avancée qui ne doit être configurée que par les services professionnels.

## Activation de la fonction {#enabling-the-feature}

Dans le menu Paramètres [!DNL Marketo Measure], accédez à la page Champs de point de contact . De là, vous pouvez activer la fonction en sélectionnant **Oui** sous **Activer les champs calculés**. Une fois la fonction activée, vous pouvez créer des champs de point de contact.

![Page des paramètres Champs de point de contact avec l’option Activer les champs calculés](assets/one.png)

## Comment {#how-to}

Pour créer un champ calculé, gardez à l’esprit qu’un utilisateur peut effectuer trois actions différentes : extraire, mapper à et concaténer. Ils sont également appelés opérateurs pour la définition d’un champ calculé.

### Extraits {#extracts}

L’opérateur [!UICONTROL extrait] extrait la valeur d’un champ à partir d’un autre emplacement, tel que : un champ Campagne, un champ Lead ou, dans un cas d’utilisation plus avancé, extrayez les paramètres personnalisés de la page de destination. Il la place ensuite sur un champ de point de contact.

**Exemple de #1**

Il existe un champ personnalisé sur le contact, campaign_source__c, que le client souhaite déposer sur le point de contact à des fins de création de rapports. Vous pouvez définir une règle pour créer un champ calculé appelé « Source de campagne » et déposer la valeur dans ce champ.

Objectif : utilisez la valeur d’un champ personnalisé et placez-le sur l’objet Touchpoint pour faciliter la création de rapports.

* Créez un champ calculé et libellez-le « Source de campagne »
* Définissez la règle en commençant par rechercher le champ Contact.Campaign_Source__c
* Utilisez l’opérateur « extracts », car nous devons extraire la valeur du paramètre .
* Pour extraire la chaîne complète du champ , nous utiliserons l’expression « (.&#42;) »

   * **(** marque le début de l’extraction)
   * **)** marque la fin de l’extraction
   * **.&#42;** nous indique que nous extrayons la chaîne complète

![Configuration des champs calculés pour l’extraction des champs Source de Campaign](assets/two.png)

**Exemple de #2**

Cette fonctionnalité permet généralement d’extraire des valeurs des paramètres personnalisés d’une chaîne d’URL. Cela s’avère utile si vous utilisez des paramètres autres que les UTM, mais que vous souhaitez analyser les valeurs sur les champs de point de contact.

**Lien :** `https://www.adobe.com/blog/marketing-revenue-reporting-overview?promo=5OFF` ou `https://www.adobe.com/blog/marketing-revenue-reporting-overview?promo=25OFF`.\
**Objectif :** créez un champ personnalisé appelé « Code de remise » et déposez la valeur « 5OFF » ou « 25OFF », quelle que soit la valeur transmise.

* Créez un champ calculé et libellez-le « Code remise »
* Définissez la règle en commençant par rechercher le champ Touchpoint.Session.LandingPage .
* Utilisez l’opérateur « extracts », car nous devons extraire la valeur du paramètre .
* Pour extraire la valeur de la promotion, nous définirons la valeur comme « promo=(\w+) »

   * **(** marque le début de l’extraction)
   * **)** marque la fin de l’extraction
   * **\w** nous indique que nous extrayons un « mot » qui inclut 0-9
   * **+** extrait la valeur complète du paramètre sans limite de caractères
   * Notez que vous utilisez une barre oblique inverse et non une barre oblique inverse

![Configuration du champ Code de remise extrayant le paramètre de promotion de l’URL](assets/three.png)

**Exemple de #3**

Essayons un exemple similaire dans lequel nous extrayons un code de suivi tel que : `https://www.adobe.com/blog/marketing-revenue-reporting-overview?cid=123456`.

**Objectif :** créez un champ calculé et libellez-le « Adobe Campaign Id » avec la valeur du paramètre cid.

* Créez un champ calculé et libellez-le « Adobe Campaign Id »
* Définissez la règle en commençant par rechercher le champ Touchpoint.Session.LandingPage .
* Utilisez l’opérateur « extracts », car nous devons extraire la valeur du paramètre .
* Pour extraire la valeur « 123456 », nous définirons la valeur comme « cid=(\d{6}) »

   * **(** marque le début de l’extraction)
   * **)** marque la fin de l’extraction
   * **\d** nous indique que nous extrayons un « chiffre »
   * **{6}** correspond au nombre de caractères extraits

![Champ Adobe Campaign Id extrayant le paramètre cid à 6 chiffres](assets/four.png)

**Exemple de #4**

À mesure que vos pages de destination deviennent plus complexes et que vous disposez de plusieurs paramètres de suivi, vous devrez peut-être créer plusieurs champs de point de contact et extraire plusieurs fois des valeurs, par exemple :
`https://www.adobe.com/blog/marketing-revenue-reporting-overview?trackID=123456&country=US&campaign_ID=7890`.

**Objectif :** créez plusieurs champs calculés pour « Pays cible » et « Identifiant de campagne personnalisé » avec les valeurs respectives des paramètres .

* Créez un champ calculé et libellez-le « Pays cible »
* Définissez la règle en commençant par rechercher le champ Touchpoint.Session.LandingPage .
* Utilisez l’opérateur « extracts », car nous devons extraire la valeur du paramètre .
* Pour extraire la valeur « US », nous définirons la valeur comme « country=(\w{2}) »

   * **(** marque le début de l’extraction)
   * **)** marque la fin de l’extraction
   * **\w** nous indique que nous extrayons un « mot »
   * **{2}** correspond au nombre de caractères extraits

* Créez un champ calculé et libellez-le « Identifiant de campagne personnalisé »
* Définissez la règle en commençant par rechercher le champ Touchpoint.Session.LandingPage .
* Utilisez l’opérateur « extracts », car nous devons extraire la valeur du paramètre .
* Pour extraire la valeur « 123456 », nous définirons la valeur comme « campaign_ID=(\d{6}) »

   * **(** marque le début de l’extraction)
   * **)** marque la fin de l’extraction
   * **\d** nous indique que nous extrayons un « chiffre »
   * **{6}** correspond au nombre de caractères extraits

![Plusieurs champs calculés extrayant les paramètres d’identifiant de pays et de campagne](assets/five.png)

### Associe à {#maps-to}

L’opérateur [!UICONTROL mappe à] crée une table de valeurs qui doivent être traduites ou regroupées dans une autre valeur. En règle générale, elle se présente sous la forme d’une valeur de clé où un code représente un nom convivial et doit être mappé à ce nom convivial.

**Exemple de #1**

Vous avez créé des campagnes pour une « promotion de fin d’été » et une « promotion du Vendredi noir » qui s’exécutent sur plusieurs canaux. Vous souhaitez créer un champ calculé appelé « Initiative » et mapper tous les points de contact avec une « promotion de fin d’été » ou une « promotion du Vendredi fou » à une valeur d’initiative telle que « Promotions », en plus d’autres valeurs possibles.

![Campagnes de mappage des champs d’initiative aux catégories de promotion](assets/six.png)

**Exemple de #2**

Maintenant que nous avons appris à extraire et à mapper aux champs, combinons ces actions afin d’abord d’extraire une valeur d’un paramètre, puis de la mapper à un nom convivial un peu plus logique. Commençons donc par cette page de destination : `https://www.adobe.com/blog/marketing-revenue-reporting-overview?BZ=04-01-09-03-10`.

**Objectif :** créez plusieurs champs calculés où le premier nombre correspond à une région, le second à un produit, le troisième à une initiative, le quatrième à un persona et le cinquième à une plateforme multimédia. Ensuite, mappez la valeur numérique à un « nom convivial ».

* Créez un champ calculé et libellez-le « Région »
* Définissez la règle en commençant par rechercher le champ Touchpoint.Session.LandingPage .
* Utilisez l’opérateur « [!UICONTROL extracts] », car nous devons extraire la valeur du paramètre .
* Pour extraire la valeur « 04 », nous définirons la valeur comme « BZ=(\d{2})-\d{2}-\d{2}-\d{2}-\d{2}-\d{2} »

   * **(** marque le début de l’extraction)

      * Notez que puisque nous extrayons uniquement les 4, seuls les premiers chiffres ont la parenthèse ouverte
   * **)** marque la fin de l’extraction

      * Notez que puisque nous extrayons uniquement les 4, seuls les premiers chiffres ont la parenthèse fermée
   * **\d** nous indique que nous extrayons un « chiffre »
   * **{2}** correspond au nombre de caractères extraits

* Cliquez sur [!UICONTROL Enregistrer]. Vous devez enregistrer votre nouveau champ avant de pouvoir l’utiliser pour la règle suivante.
* Ensuite, nous allons mapper toutes les valeurs possibles pour les premiers chiffres à ses noms conviviaux
* Créez un champ calculé et libellez-le « Nom_Région »
* Définissez la règle en commençant par rechercher le champ extrait. Dans ce cas, [!DNL Touchpoint.Region]
* Utilisez l’opérateur « [!UICONTROL mappe à] », car nous voulons créer un mappage pour chaque nombre à sa valeur
* Un tableau vous est présenté pour répertorier chaque mappage. Au bout du compte, voici à quoi il ressemblera :
* En fonction du mappage et de l’URL ci-dessus, la valeur « Region_Value » pour un point de contact avec cette page de destination est « EMEA »
* Répétez l’extraction et le mappage pour les 4 ensembles de chiffres restants

   * Pour extraire la valeur 01, définissez la valeur comme « BZ=\d{2}-**(\d{2})**-\d{2}-\d{2}-\d{2} »
   * Pour extraire le 09, définissez la valeur comme « BZ=\d{2}-\d{2}-**(\d{2})**-\d{2}-\d{2} »
   * Pour extraire le 03, définissez la valeur comme « BZ=\d{2}-\d{2}-\d{2}-**(\d{2})**-\d{2} »
   * Pour extraire le 10, vous devez définir la valeur comme « BZ=\d{2}-\d{2}-\d{2}-\d{2}-**(\d{2})** »

![Table de mappage des noms de région avec des codes numériques aux noms de région](assets/seven.png)

### Concatène {#concatenates}

L’opérateur [!UICONTROL concatène] combine les valeurs de plusieurs champs en un seul champ. Cela s’avère utile pour créer une valeur personnalisée qui extrait des données dans différents champs afin de :

**Exemple de #1**

Il existe des champs distincts sur l’objet d’opportunité pour Segment__c et Grade__c que l’utilisateur souhaite combiner en un seul champ sur l’objet de point de contact à des fins de création de rapports. En concaténant les champs, vous verrez des valeurs telles que Enterprise_A ou Mid-Market_B.

![Configuration de concaténation combinant les champs Segment et Grade](assets/eight.png)

## Champs et segments de point de contact {#touchpoint-fields-and-segments}

Maintenant que les valeurs de votre URL ont été analysées et existent sur le point de contact, vous verrez les nouveaux champs là où les champs de point de contact sont utilisés, comme la création de segments ou la définition de règles de suppression de point de contact.

Cette version de produit offre la possibilité de créer des segments à l’aide de champs de point de contact. Les segments n’ont pas pu être créés avec les champs de point de contact précédents.

![Interface de création de segment affichant les champs de point de contact disponibles](assets/nine.png)

Pour faciliter la création de segments, il est désormais possible de créer des segments dynamiques à partir des champs de point de contact qui ont été créés. Par exemple, si vous avez créé un champ de point de contact qui analyse une région géographique, plutôt que de créer un segment pour chaque région possible, vous pouvez configurer un segment et nous créerons des segments pour chaque instance où une nouvelle valeur s’affiche. Cela s’avère extrêmement utile si un attribut tel qu’un code postal doit être analysé et utilisé comme segment.

La configuration ressemblerait à la capture d’écran ci-dessous. Le nom du segment extrait dynamiquement la valeur du champ de point de contact à l’aide des accolades pour rechercher votre champ.

![Configuration de segment dynamique avec référence de champ crochet](assets/ten.png)

La règle fait référence au même champ de point de contact et recherche les valeurs « différentes de null ».

![Règle de segment avec une condition différente de null](assets/eleven.png)

## Questions fréquentes {#faq}

**Y a-t-il un nombre maximal de champs de point de contact que nous pouvons créer ?**

Il existe une limite de 100 champs.

**Je ne vois pas mon nouveau champ de point de contact que je viens de créer dans la liste de sélection. Où est-il ?**

N’oubliez pas d’enregistrer vos règles après l’avoir créées. Si votre nouveau champ ne s’affiche pas, vérifiez si vous avez enregistré. Vous devez enregistrer votre nouveau champ avant de pouvoir l’utiliser pour la règle suivante.

>[!NOTE]
>En raison du niveau de complexité, un champ de point de contact qui utilise l’opérateur « mappe à » n’est pas disponible pour être utilisé dans un autre champ de point de contact.

**Quelle expression dois-je utiliser pour extraire plusieurs paramètres d’une seule landing page ?**

Comme dans l’exemple d’extraction #4, vous devez créer plusieurs champs pour extraire chacun des paramètres. Ainsi, si vous disposez de cinq valeurs différentes, vous allez créer cinq champs de point de contact pour extraire chacune d’elles.

**Pourquoi mes nouveaux champs ne s’affichent-ils pas dans le schéma [!DNL Marketo Measure] ?**

Un travail supplémentaire est nécessaire pour exposer les nouveaux champs dans le schéma Data Warehouse [!DNL Marketo Measure]. Actuellement, les champs sont exposés par le biais des paramètres et de la configuration afin que vous puissiez utiliser les champs de point de contact dans la création de segments ou la création de règles de suppression de point de contact.

**Comment puis-je vérifier que mon expression d’extrait est valide et extraire la valeur correcte ?**

Il existe un outil en ligne ([[!DNL https] ://regex101.com/](https://regex101.com/){target="_blank"}) que vous pouvez exécuter et tester l’expression. L’expression apparaît en vert si elle est valide ou en rouge si elle n’est pas valide. En outre, la zone [!UICONTROL explication] en haut à droite est utile et vous indique ce que vous extrayez.

![Outil de validation Regex affichant une expression valide en vert](assets/twelve.png)

![Outil de validation Regex affichant une expression non valide en rouge](assets/thirteen.png)
