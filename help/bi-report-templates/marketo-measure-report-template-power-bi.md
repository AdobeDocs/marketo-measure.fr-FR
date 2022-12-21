---
description: "[!DNL Marketo Measure] Modèle de rapport - Power BI - [!DNL Marketo Measure] - Documentation du produit"
title: "[!DNL Marketo Measure] Modèle de rapport - Power BI"
exl-id: c296b8f9-4033-4723-9a71-63a458640d27
source-git-commit: 65e7f8bc198ceba2f873ded23c94601080ad0546
workflow-type: tm+mt
source-wordcount: '2583'
ht-degree: 1%

---

# [!DNL Marketo Measure] Modèle de rapport - Power BI {#marketo-measure-report-template-power-bi}

## Démarrer {#getting-started}

Vous pouvez accéder au modèle de rapport de Power BI [here](https://github.com/adobe/Marketo-Measure-BI-Templates){target=&quot;_blank&quot;}.

Ouvrir l’Adobe [!DNL Marketo Measure] Fichier de Power BI de modèle de création de rapports.

![](assets/marketo-measure-report-template-power-bi-1.png)

Vous trouverez vos informations spécifiques sur le serveur, l’entrepôt et le schéma dans la section [!DNL Marketo Measure] de l’interface utilisateur de [!DNL Data Warehouse] page d’informations. Les instructions pour localiser cette page sont détaillées. [here](/help/marketo-measure-data-warehouse/data-warehouse-access-reader-account.md){target=&quot;_blank&quot;}.

Les paramètres QueryFilterStartDate et QueryFilterEndDate permettent de limiter la quantité de données importées. Ces paramètres doivent être au format SQL comme ils sont utilisés dans les requêtes envoyées à [!DNL Snowflake]. Par exemple, si vous souhaitez limiter les données aux deux dernières années, QueryFilterStartDate sera dateadd (year,-2,current_date()). Ces paramètres sont comparés aux types de données datetime. Il est donc recommandé d’utiliser dateadd (day,1,current_date()) pour que QueryFilterEndDate renvoie toutes les données à l’heure actuelle.

## Connexion aux données {#data-connection}

Les paramètres saisis lors de l’ouverture du fichier sont utilisés pour structurer les requêtes natives qui importent des tableaux à partir de l’entrepôt de données. Vous devrez toujours configurer une connexion de données à votre [!DNL Snowflake] instance. Pour ce faire, vous aurez besoin des mêmes noms de serveur et d’entrepôt, ainsi que de vos nom d’utilisateur et mot de passe. Vous trouverez des informations détaillées sur l’emplacement de votre nom d’utilisateur et la réinitialisation de votre mot de passe, le cas échéant. [here](/help/marketo-measure-data-warehouse/data-warehouse-access-reader-account.md){target=&quot;_blank&quot;}.

## Importation de données {#data-import}

Afin d’améliorer les performances des rapports et de tirer parti des fonctionnalités de transformation de Power Query, nous avons choisi de configurer ce modèle à l’aide de la méthode de stockage d’importation.

### Paramètres de requête {#query-parameters}

Pour limiter les données importées dans le modèle, chaque table est configurée en utilisant une requête native comme source. Les requêtes natives doivent être approuvées pour s’exécuter. Vous devrez cliquer sur Exécuter pour chaque requête. Cette étape n’est nécessaire que lors de la première exécution des requêtes ou si les paramètres changent.

![](assets/marketo-measure-report-template-power-bi-2.png)

Toutes les requêtes filtrent les lignes supprimées et la variable [!UICONTROL facts] Les tableaux sont définis pour filtrer les lignes avec une date de modification entre les dates de début et de fin renseignées en tant que paramètres.

>[!NOTE]
>
>Les filtres de date étant appliqués à la date de modification d’une ligne, soyez prudent lorsque vous créez des rapports sur des dates qui se situent en dehors de la plage de dates limitée. Par exemple, la période modifiée est limitée aux deux dernières années. Cela peut inclure un événement avec une date d’événement d’il y a trois ans, mais qui a été modifié récemment. Toutefois, les rapports sur les événements d’il y a trois ans renverront des résultats incomplets, car toutes les lignes n’auront pas été modifiées au cours de la période de deux ans.

![](assets/marketo-measure-report-template-power-bi-3.png)

Les tableaux suivants sont traités comme des tableaux de faits; les limites de date à la date de modification ont été ajoutées à ces requêtes.

* Activité
* Touchpoint
* Point de contact de piste
* Point de contact d’attribution
* Coût
* Formulaire de site
* Session
* Membre de la campagne
* Tâche
* Événement
* Transition de l’étape de piste/contact
* Transition de l’étape d’opportunité

Les tableaux suivants sont traités comme des tableaux de dimension ; aucune limite de date n’est définie pour ces requêtes.

* Compte
* Campagne
* Contact
* Taux de conversion
* Opportunité
* Lead
* Étape
* Canal

## Transformations de données {#data-transformations}

Quelques transformations ont été appliquées aux données dans Power Query. Pour afficher les transformations spécifiques d’un tableau, ouvrez Power Query, accédez à un tableau, puis notez les étapes appliquées sur le côté gauche de la fenêtre. Certaines des transformations spécifiques sont décrites ci-dessous.

![](assets/marketo-measure-report-template-power-bi-4.png)

### Colonnes supprimées {#removed-columns}

Pour simplifier le modèle de données et supprimer les données redondantes et inutiles, nous avons réduit le nombre de colonnes importées dans Power BI à partir de la [!DNL Snowflake] table. Les colonnes supprimées comprennent les clés étrangères inutiles, les données dénormalisées mieux exploitées par le biais de relations avec d’autres tables dans le modèle, les colonnes de contrôle et les champs utilisés pour les [!DNL Marketo Measure] traitement. Vous pouvez ajouter ou supprimer des colonnes en fonction des besoins de votre entreprise. Accédez à l’étape &quot;Autres colonnes supprimées&quot; après l’étape &quot;Source&quot; dans n’importe quel tableau, cliquez sur l’icône en forme d’engrenage, puis mettez à jour les colonnes sélectionnées dans la liste fournie.

>[!NOTE]
>
>* Soyez prudent lors de l’ajout de valeurs de clé étrangère supplémentaires. Power BI est souvent défini pour détecter automatiquement les relations dans le modèle et l’ajout de valeurs de clé étrangère peut entraîner des liens indésirables entre les tables et/ou désactiver les relations existantes.
>
>* La plupart des tableaux de la variable [!DNL Marketo Measure] Data Warehouse contient des données dimensionnelles dénormalisées. Nous avons travaillé à normaliser et nettoyer le modèle dans la Power BI autant que possible afin d’améliorer les performances et la précision des données. Soyez prudent lorsque vous incluez des champs dénormalisés supplémentaires dans les tableaux de faits, cela peut rompre le filtrage dimensionnel dans les tableaux et générer des rapports inexacts.



![](assets/marketo-measure-report-template-power-bi-5.png)

### Colonnes renommées {#renamed-columns}

Les tableaux et les colonnes ont été renommés afin de les rendre plus conviviaux et de normaliser les conventions d’appellation. Pour afficher les modifications apportées au nom de la colonne, accédez à l’étape &quot;Colonnes renommées&quot; après l’étape &quot;Autres colonnes supprimées&quot; d’un tableau.

![](assets/marketo-measure-report-template-power-bi-6.png)

### Segments renommés {#renamed-segments}

Les noms de segment pouvant être personnalisés, ils comportent des noms de colonne génériques dans l’entrepôt de données du Snowflake. [!DNL BIZ_SEGMENT_NAMES] est un tableau de mappage qui répertorie le nom du segment générique et son nom de segment personnalisé mappé, défini dans la section de segment dans la variable [!DNL Marketo Measure] Interface utilisateur. La table Nom de segment est utilisée pour renommer les colonnes de segments dans les tableaux Point de contact de piste et Point de contact d’attribution. S’il n’existe aucun segment personnalisé, le nom du segment générique reste.

![](assets/marketo-measure-report-template-power-bi-7.png)

### Conversion d’ID sensible à la casse {#case-sensitive-id-conversion}

[!DNL Marketo Measure] Les données comportent deux tableaux où les valeurs de clé Principale (ID) sont sensibles à la casse, à savoir Point de contact et Campaign. Le moteur de données qui génère la couche de modélisation de Power BI n’est pas sensible à la casse, ce qui entraîne des valeurs d’identifiant &quot;en double&quot;. Pour préserver la sensibilité à la casse de ces valeurs clés, nous avons mis en oeuvre des étapes de transformation qui associent des caractères invisibles aux caractères en minuscules, tout en préservant l’unicité de l’identifiant lors de l’évaluation dans la couche du moteur de données. Vous trouverez plus de détails sur le problème et les étapes détaillées sur la méthode que nous avons utilisée. [here] (https://blog.crossjoin.co.uk/2019){target=&quot;_blank&quot;}. Ces valeurs d’identifiant sensibles à la casse sont étiquetées comme &quot;identifiants de jointure&quot; et sont utilisées comme clés de jointure dans la couche de relation. Nous avons masqué les identifiants de jointure dans la couche de création de rapports, en conservant les valeurs d’identifiants d’origine visibles pour une utilisation dans les rapports, puisque les caractères invisibles peuvent interférer avec les fonctions de découpe/collage et le filtrage.

![](assets/marketo-measure-report-template-power-bi-8.png)

![](assets/marketo-measure-report-template-power-bi-9.png)

### Lignes ajoutées {#rows-added}

Pour ajouter des fonctionnalités de conversion de devise aux calculs dans le modèle, nous avons ajouté une colonne de taux de conversion d’entreprise aux tableaux Opportunité et Coût . La valeur de cette colonne est ajoutée au niveau de la ligne et évaluée en se joignant au tableau Taux de conversion à la date et à l’ID de devise. Pour plus d’informations sur le fonctionnement de la conversion de devise dans ce modèle, voir [Conversion de devise](#currency-conversion) dans cette documentation.

![](assets/marketo-measure-report-template-power-bi-10.png)

Le tableau Taux de conversion stocké dans [!DNL Snowflake] contient une plage de dates pour chaque conversion. Power BI n’autorise pas les critères de jointure sur un calcul (c’est-à-dire entre une plage de dates). Afin de rejoindre à la date, nous avons ajouté des étapes au tableau Taux de conversion afin de développer les lignes de sorte qu’il y ait une ligne pour chaque date de la période de conversion.

![](assets/marketo-measure-report-template-power-bi-11.png)

## Modèle de données {#data-model}

Cliquez sur l’image ci-dessous pour sa version agrandie.

[![](assets/marketo-measure-report-template-power-bi-12.png)](/help/bi-report-templates/assets/power-bi-data-model.png){target=&quot;_blank&quot;}

### Relations et flux de données {#relationships-and-data-flow}

Les données d’événement, utilisées pour créer des points de contact, sont stockées dans la variable [!UICONTROL Session], [!UICONTROL Tâche], [!UICONTROL Événement], [!UICONTROL Activité]et les tables des membres de Campaign. Ces tables d’événements se joignent à la table Point de contact par l’intermédiaire de leurs identifiants respectifs. Si l’événement a entraîné un point de contact, les détails sont stockés dans la table Point de contact.

Les points de contact de piste et d’attribution sont stockés dans leurs propres tables, avec un lien vers la table des points de contact. La plupart des données dimensionnelles des points de contact de piste et d’attribution proviennent de leur lien vers le point de contact correspondant.

Dans ce modèle, les dimensions Campagne et Canal sont liées au point de contact. Par conséquent, tous les rapports sur ces dimensions sont générés par ce lien et signifie que les rapports dimensionnels sur les données d’événement peuvent être incomplets. En effet, de nombreux événements ne comportent de liens vers ces dimensions qu’après leur traitement dans les points de contact. Remarque : certains événements, tels que les sessions, comportent des liens directs vers les dimensions Campagne et Canal. Si vous souhaitez créer des rapports au niveau de la session sur ces dimensions, il est recommandé de créer un modèle de données distinct à cet effet.

Les données de coût sont stockées à différents niveaux d’agrégation dans la variable [!DNL Snowflake] tableau Coût de l’entrepôt de données. Pour tous les fournisseurs d&#39;annonces, les données au niveau de la campagne peuvent être cumulées au niveau du canal. Pour cette raison, ce modèle extrait les données de coût en fonction de l’indicateur &quot;campaign_is_aggatable_cost&quot;. Les coûts auto-déclarés peuvent être envoyés au niveau du canal uniquement et ne sont pas nécessaires pour disposer de données Campaign. Pour fournir un rapport de coûts le plus précis possible, les coûts auto-déclarés sont extraits en fonction de l’indicateur &quot;channel_is_aggatable_cost&quot;. La requête qui importe les données de coût est écrite avec la logique suivante : Si ad_provider = &quot;SelfReported&quot; alors channel_is_aggatable_cost = true, else campaign_is_aggatable_cost = true.

Les données de coût et les données de point de contact ont des dimensions communes. Par conséquent, les deux tableaux de faits ont des relations avec les tableaux de dimension Campagne et Canal .

Dans le contexte de ce modèle, [!UICONTROL prospect], [!UICONTROL Contact], [!UICONTROL Compte], et [!UICONTROL Opportunité] Les données sont considérées comme des données dimensionnelles et sont associées directement à la variable [!UICONTROL prospect] Point de contact et [!UICONTROL Attribution] Tables de points de contact.

### Ajout de tableaux {#added-tables}

**Date**

Dans la mesure où Power BI autorise uniquement les relations entre les tables sur une colonne, un tableau de dimension Date a été ajouté afin de faciliter la jointure nécessaire entre les tables contenant les montants (opportunités et coûts) et le tableau Taux de conversion. Pour plus d’informations sur le mode de calcul des conversions de devises dans ce modèle, reportez-vous à la section Conversion de devise .

**Mesures**

Toutes les mesures ont été ajoutées à un tableau dédié Mesures . Il n’est pas connecté au modèle, mais sert d’emplacement unique pour stocker toutes les mesures, pour en faciliter l’utilisation.

**Modèle d’attribution**

Un tableau distinct a été ajouté pour stocker les noms des modèles d’attribution. Ce tableau est utilisé pour créer des filtres qui permettent à l’utilisateur de basculer entre les modèles d’attribution pour le calcul des recettes attribuées.

### Conversion de devise {#currency-conversion}

Les taux dans le tableau Taux de conversion représentent la valeur nécessaire pour convertir un montant à partir de la devise de l’entreprise. Les conversions vers n’importe quelle devise nécessitent une double conversion, d’abord de la devise d’origine vers la devise de l’entreprise, puis de la devise de l’entreprise vers la devise sélectionnée. La première étape de cette chaîne dans le modèle consiste à ajouter une colonne avec le taux de conversion de l’entreprise aux tables avec les montants, les opportunités et le coût. Ces étapes sont détaillées dans l’en-tête Lignes ajoutées de la section Transformations de données de ce document. La conversion de la devise d’origine vers la devise de l’entreprise consiste à diviser la valeur par cette colonne ajoutée. L&#39;étape suivante consiste à multiplier la valeur de la devise de l&#39;entreprise par le taux dans le tableau Taux de conversion , qui correspond à la devise sélectionnée.

* Convertir la valeur d’origine en valeur de devise de l’entreprise/taux de conversion de l’entreprise = valeur en devise de l’entreprise
* Convertir la valeur de la devise de l’entreprise en valeur de devise sélectionnée dans la devise de l’entreprise `*` taux de conversion de la devise sélectionnée = valeur dans la devise sélectionnée

Étant donné que les taux de conversion ne doivent pas être statiques et peuvent varier selon des périodes spécifiées, tous les calculs de conversion de devise doivent être effectués au niveau de la ligne. Ici encore, dans la mesure où les taux de conversion se rapportent à une période spécifique, le calcul de recherche doit être effectué dans le DAX de la mesure, de sorte que la relation puisse être définie à la fois sur le code de devise et sur la date.

Les mesures de conversion de devise de ce modèle remplacent le taux par une valeur de 1,0 si aucun taux de conversion ne peut être identifié. Des mesures distinctes ont été créées pour afficher la valeur de la devise de la mesure. Une alerte s’affiche si un calcul comprend plusieurs valeurs monétaires (c’est-à-dire qu’une valeur n’a pas pu être convertie dans la devise sélectionnée) a été créée.

![](assets/marketo-measure-report-template-power-bi-13.png)

## Définitions des données {#data-definitions}

Des définitions ont été ajoutées au modèle de Power BI pour les tableaux, les colonnes personnalisées et les mesures.

![](assets/marketo-measure-report-template-power-bi-14.png)

![](assets/marketo-measure-report-template-power-bi-15.png)

![](assets/marketo-measure-report-template-power-bi-16.png)

Pour afficher les définitions des colonnes provenant directement de [!DNL Snowflake], reportez-vous à la section [documentation de l’entrepôt de données](/help/marketo-measure-data-warehouse/data-warehouse-schema.md){target=&quot;_blank&quot;}

## Incohérences entre les modèles et Discover {#discrepancies-between-templates-and-discover}

### Chiffre d’affaires attribué {#attributed-revenue}

Les points de contact de piste et les points de contact d’attribution héritent des données dimensionnelles du point de contact d’origine. Le modèle de rapport source toutes les données dimensionnelles héritées de la relation au point de contact, tandis que dans le modèle Discover, les données dimensionnelles sont dénormalisées en fonction des enregistrements Point de contact de piste et d’attribution. Les recettes totales attribuées ou les valeurs de recettes de pipeline attribuées doivent correspondre entre les deux rapports. Cependant, des incohérences peuvent être observées lorsque les recettes sont ventilées ou filtrées par données dimensionnelles (canal, sous-canal ou campagne). Si les recettes dimensionnelles ne correspondent pas entre le modèle et Discover, il est probable qu’il manque des enregistrements de point de contact dans le jeu de données du rapport de modèle. Cela se produit lorsqu’il existe un enregistrement Point de contact de piste ou d’attribution, mais qu’aucun enregistrement correspondant n’est présent dans le tableau Points de contact du jeu de données importé dans le rapport. Comme ces tables sont filtrées par date de modification, il est possible que l’enregistrement Point de contact de piste/attribution ait été modifié plus récemment que l’enregistrement Point de contact. Par conséquent, le point de contact de piste/attribution a été importé dans le jeu de données alors que l’enregistrement Point de contact d’origine ne l’était pas. Pour résoudre ce problème, élargissez la période filtrée du tableau Point de contact ou envisagez de supprimer la contrainte de date dans son ensemble. Remarque : Le point de contact est un tableau volumineux. Il faut donc tenir compte des compromis entre un jeu de données plus complet et la quantité de données à importer.

### Coût {#cost}

La création de rapports de coûts dans les modèles n’est disponible qu’aux niveaux de la campagne et du canal. Toutefois, Discover offre la création de rapports aux niveaux de granularité inférieurs pour certains fournisseurs d’annonces (c’est-à-dire créatifs, mots-clés, groupes d’annonces, etc.). Pour plus d’informations sur la manière dont les données de coût sont modélisées dans les modèles, reportez-vous à la section Modèle de données de cette documentation. Si la dimension est filtrée dans [!UICONTROL Discover] est définie sur canal ou campagne, les coûts au niveau du canal, du sous-canal et de la campagne doivent s’aligner entre Discover et les modèles de rapport.

### RSI {#roi}

Comme le ROI est calculé à partir des recettes et des coûts attribués, les mêmes incohérences qui peuvent survenir dans l’un de ces calculs peuvent apparaître dans le ROI et pour les mêmes raisons, comme indiqué dans ces sections.

### Points de contact {#touchpoints}

Ces mesures, comme indiqué dans les modèles de rapport, ne sont pas reflétées dans Discover. Il n’existe actuellement aucune comparaison directe entre les deux.

### Trafic Web {#web-traffic}

Le modèle de données de rapport normalise les données des dimensions des canaux, des sous-canaux et des campagnes au moyen de la relation entre la session et le point de contact. Il diffère du modèle de données de Discover , qui dénormalise ces dimensions en session. En raison de cette distinction, les comptes globaux des visites et des visiteurs doivent correspondre entre Discover et le modèle de rapport. Toutefois, une fois affichés ou filtrés par dimension, ces chiffres ne doivent pas s’aligner. En effet, les données dimensionnelles du modèle ne sont disponibles que pour les événements web qui ont généré un point de contact (c’est-à-dire des événements non anonymes). Pour plus d’informations, reportez-vous à la section [Modèle de données](#data-model) de cette documentation.

Il peut y avoir de légères différences dans le nombre total de formulaires du site entre [!DNL Discover] et le modèle. En effet, le modèle de données du modèle de rapport obtient des données dimensionnelles pour le formulaire du site par le biais d’une relation avec Session, puis avec Point de contact ; il existe quelques cas où les données de formulaire de site n’ont pas de session en corrélation.

### Prospects et comptes {#leads-and-accounts}

La création de rapports dimensionnels pour les comptes concernés peut différer légèrement entre Discover et le modèle. Cela est dû à la modélisation dimensionnelle issue de la relation entre le point de contact et le point de contact de piste ou le point de contact d’attribution. Pour plus d’informations, reportez-vous aux détails décrits dans la section Recettes affectées .

Tous les comptes de piste dans Discover se voient attribuer le nombre de pistes et dans le modèle de rapport, la mesure est touchée. Il n&#39;y a donc pas de comparaison directe entre les deux rapports pour cette mesure.

### Parcours d’engagement {#engagement-path}

Il n’existe aucune comparaison directe entre la variable [!UICONTROL Chemin de l’engagement] dans Discover et le modèle. Le rapport dans [!DNL Discover] est modélisé à partir du point de contact, tandis que le rapport du modèle est modélisé à partir du point de contact d’attribution. Le modèle se concentre uniquement sur les opportunités et leurs points de contact associés au lieu d’afficher toutes les données de point de contact.

### Vitesse de transaction {#deal-velocity}

Il ne doit pas y avoir d’incohérence entre ce rapport dans le modèle et la mosaïque Vitesse de transaction dans le tableau de bord Velocity de Discover.
