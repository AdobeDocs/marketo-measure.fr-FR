---
unique-page-id: 18874656
description: Filtres - [!DNL Marketo Measure] - Documentation du produit
title: Filtres
exl-id: 249266c8-9ff5-4895-979c-4f377423d031
feature: Reporting
source-git-commit: 8ac315e7c4110d14811e77ef0586bd663ea1f8ab
workflow-type: tm+mt
source-wordcount: '1290'
ht-degree: 3%

---

# Filtres {#filters}

Découvrez les différents filtres disponibles dans Discover et comment les utiliser.

>[!NOTE]
>
>Les opérateurs &quot;correspond à un attribut utilisateur&quot; et &quot;correspond à (avancé)&quot; de vos filtres Discover sont purement administratifs et peuvent être ignorés en toute sécurité.

**ID de compte**

_Utilisé dans : Marketing basé sur les comptes_

Sélectionnez ou collez dans une série d’identifiants de compte du CRM pour filtrer les résultats. Les identifiants de compte offrent davantage d’unicité que le nom de compte, car les noms peuvent être identiques.

**Nom du compte**

_Utilisé dans : Marketing basé sur les comptes_

Sélectionnez ou collez dans une série de noms de compte du CRM pour filtrer les résultats. Les chaînes peuvent avoir des doublons, il est donc possible d’avoir plusieurs &quot;[!DNL Marketo Measure]&quot;, par exemple. Si un compte unique est nécessaire dans ce cas, utilisez plutôt le filtre Identifiant de compte .

**Modèle d’attribution**

_Utilisé dans : Présentation, Dépenses marketing, RSI des publicités, Marketing Basé Sur Un Compte, Trafic Web, CMO, Média Payé, Marketing De Contenu, Passport_

Choisissez un modèle d’attribution unique à appliquer au panorama : Première touche, Première touche de création de piste, En forme de U, En forme de W, Chemin complet ou Modèle personnalisé. Le chemin complet et le modèle personnalisé ne sont pas disponibles sur tous les niveaux.

**Campagne**

_Utilisé dans : Aperçu, Croissance, RSI des publicités, Trafic web, CMO, Média payant, Marketing de contenu, Passeport_

Vous pouvez filtrer le panorama selon un ou plusieurs noms de campagne. Les opérateurs donnent au filtre une flexibilité supplémentaire, comme l&#39;utilisation des opérateurs &quot;contient&quot; ou &quot;commence par&quot;. Si un filtre Canal ou Sous-canal a été appliqué, la liste des campagnes qui s’affichent sera un sous-ensemble des filtres appliqués.

**Catégorie 1-10**

_Utilisé dans : Aperçu, Croissance, RSI des publicités, CMO, Média payant, Marketing du contenu, Vitesse, Instantané, Entonnoir de cohortes, Passeport_

Appliquez des filtres de segments au panorama à l’aide des catégories et des segments que vous avez créés dans la [!DNL Marketo Measure] Paramètres. La liste des catégories que vous avez créées s’affiche dans le menu Filtres. Ainsi, si aucune catégorie n’a été configurée, aucun filtre de catégorie n’apparaît dans le menu. Les catégories de segments ne sont pas disponibles dans tous les niveaux et le nombre de catégories disponibles varie également en fonction du niveau.

**Canal**

_Utilisé dans : Présentation, Croissance, Dépenses marketing, RSI des publicités, Trafic web, CMO, Média payant, Marketing de contenu, Velocity, Passport_

Vous pouvez filtrer le panorama selon un ou plusieurs canaux. Les opérateurs donnent au filtre une flexibilité supplémentaire, comme l&#39;utilisation des opérateurs &quot;contient&quot; ou &quot;commence par&quot;. Une fois un canal saisi, les valeurs affichées dans les filtres Sous-canal et Campagne proviennent du filtre sous-canal appliqué.

**Étape de la cohorte**

_Utilisé dans : entonnoir de cohortes_

Sélectionnez la scène dont vous souhaitez afficher une cohorte. La scène que vous sélectionnez s’affiche en haut de l’entonnoir, avec toutes les conversions qui descendent du haut.

**Date**

_Utilisé dans : Aperçu, Croissance, Dépenses marketing, RSI des publicités, Marketing Basé Sur Les Comptes, Trafic Web, CMO, Média Payé, Marketing De Contenu, Vitesse, Instantané, Entonnoir De Cohorte, Passport_

Sélectionnez une plage de dates pour filtrer les données des panoramas à l’aide d’opérateurs de dates flexibles tels que &quot;est dans la plage&quot;, &quot;est dans l’année&quot; ou &quot;est avant&quot;, par exemple. L’exception est l’instantané, où vous sélectionnerez une seule date pour afficher un instantané des données.

**Type de date**

_Utilisé dans : Présentation, Croissance, Dépenses marketing, RSI des publicités, Marketing Basé Sur Un Compte, Trafic Web, CMO, Média Payé, Marketing De Contenu, Passport_

Choisissez le type de date à utiliser, lié au filtre Date . Le type de date par défaut varie en fonction du panorama. La date du point de contact fait référence à la date à laquelle l&#39;activité marketing a eu lieu, la date de création correspond à la date à laquelle le prospect ou le contact ou l&#39;opportunité a été créé dans le CRM, et la date de clôture est la date à laquelle l&#39;opportunité a été fermée.

**Dimension**

_Utilisé dans : Média payant_

La Dimension est similaire à la fonction Group By , sauf qu’elle est utilisée sur la carte Paid Media d’une manière légèrement différente. Au lieu d’empiler un graphique, la Dimension modifie les lignes du graphique Aperçu ainsi que l’objet au début des tableaux.

![](assets/1.png)

Par défaut, la Dimension est définie sur Sous-canal et peut être remplacée par :

* Aucun : affiche tout dans l’agrégat sans ventilation
* Canal : répertorie les données par canal marketing
* Subchannel : répertorie les données par sous-canal marketing.
* Campagne : répertorie les données par campagne.
* Compte : répertorie les données par compte. S’applique à [!DNL AdWords], [!DNL Bing], et [!DNL Facebook].
* Groupe publicitaire : répertorie les données par groupe publicitaire. S’applique à [!DNL AdWords], [!DNL Bing], et [!DNL Facebook].
* Publicité : répertorie les données par publicité. S’applique aux annonces Doubleclick. Par conséquent, si Doubleclick n’est pas utilisé, aucun résultat n’apparaîtra.
* Annonceur : répertorie les données par annonceur. S’applique à l’annonceur Doubleclick. Par conséquent, si Doubleclick n’est pas utilisé, aucun résultat ne s’affiche.
* Créatif : répertorie les données par créatif. S’applique à [!DNL AdWords], [!DNL Bing], et [!DNL Facebook].
* Mot-clé : répertorie les données par mot-clé. S’applique à [!DNL AdWords], [!DNL Bing], et [!DNL Facebook].
* Placement : répertorie les données par emplacement. S’applique aux emplacements double-clic. Par conséquent, si le double-clic n’est pas utilisé, aucun résultat n’apparaîtra.
* Site : répertorie les données par site. S’applique aux sites Doubleclick. Par conséquent, si Doubleclick n’est pas utilisé, aucun résultat n’apparaîtra.

**Grouper par**

_Utilisé dans : Présentation, Croissance, Dépenses marketing, Marketing Basé Sur Les Comptes, Trafic Web, CMO_

Ajuste les graphiques pour modifier la dimension empilée et regroupée. Par défaut, Group By est défini sur Channel et peut être remplacé par :

* Aucun : affiche tout dans l’agrégat sans ventilation
* Canal : groupe les données par canal marketing
* Subchannel : groupe les données par sous-canal marketing
* Campagne : groupe les données par campagne.
* Compte : groupe les données par compte. S’applique à [!DNL AdWords], [!DNL Bing], et [!DNL Facebook].
* Groupe publicitaire : groupe les données par groupe publicitaire. S’applique à [!DNL AdWords], [!DNL Bing], et [!DNL Facebook].
* Publicité : groupe les données par publicité. S’applique aux annonces Doubleclick. Par conséquent, si Doubleclick n’est pas utilisé, aucun résultat n’apparaîtra.
* Annonceur : groupe les données par annonceur. S’applique à l’annonceur Doubleclick. Par conséquent, si Doubleclick n’est pas utilisé, aucun résultat ne s’affiche.
* Créatif : groupe les données par créatif. S’applique à [!DNL AdWords], [!DNL Bing], et [!DNL Facebook].
* Mot-clé : groupe les données par mot-clé. S’applique à [!DNL AdWords], [!DNL Bing], et [!DNL Facebook].
* Placement : groupe les données par emplacement. S’applique aux emplacements double-clic. Par conséquent, si le double-clic n’est pas utilisé, aucun résultat n’apparaîtra.
* Site : groupe les données par site. S’applique aux sites Doubleclick. Par conséquent, si Doubleclick n’est pas utilisé, aucun résultat n’apparaîtra.

![](assets/2.png)

**Page de destination**

_Utilisé dans : Marketing de contenu_

Découvrez les performances d’une seule page d’entrée ou peut-être des pages d’entrée contenant un certain mot, par exemple &quot;blog&quot;.

**Métrique**

_Utilisé dans : Présentation, Trafic web, CMO, Média payant, Marketing de contenu_

Deux sélecteurs de mesure différents sont utilisés dans différents panoramas. Le sélecteur de mesure modifie la mesure sur un graphique, de sorte que vous puissiez basculer entre l’affichage des recettes, les dépenses ou les impressions, par exemple.

Sur les panoramas Aperçu et CMO, il existe une liste abrégée de valeurs liées aux mesures de retour sur investissement :

* Recettes
* Dépenses
* Affaires
* Chiffre d’affaires de pipeline
* Opportunités
* Contacts
* Prospects

Sur les panoramas Trafic web, Médias payants et Marketing de contenu, il existe une liste plus longue de valeurs liées aux mesures de retour sur investissement et d’entonnoir :

* Recettes
* Dépenses
* Affaires
* Chiffre d’affaires de pipeline
* Opportunités
* Contacts
* Prospects
* Clics
* impressions
* Visites
* Visites uniques
* Aperçu pages
* Formulaires

**Étape**

_Utilisé dans : Velocity_

Par défaut, la carte Vitesse affiche les heures de toutes les étapes, mais pour accéder à une étape spécifique, utilisez le filtre Etape pour sélectionner l’étape.

**Sous-canal**

_Utilisé dans : Aperçu, croissance, dépenses marketing, retour sur investissement des publicités, trafic web, CMO, média payant, marketing de contenu, port_

Vous pouvez filtrer le panorama selon un ou plusieurs sous-canaux. Les opérateurs donnent au filtre une flexibilité supplémentaire, comme l&#39;utilisation des opérateurs &quot;contient&quot; ou &quot;commence par&quot;. Si un filtre Canal a été appliqué, la liste des sous-canaux qui apparaissent sera un sous-ensemble des filtres appliqués. Une fois qu’un sous-canal est saisi, les valeurs affichées dans les filtres de campagne proviennent du filtre de sous-canal appliqué.

**URL**

_Utilisé dans : Trafic web_

Explorez le trafic d’une seule URL, ou peut-être des URL qui contiennent un certain mot tel que &quot;produit&quot;.

**Remporté**

_Utilisé dans : Velocity_

Par défaut, le panorama Velocity ne tient compte que des opportunités gagnantes fermées, mais ajustez ce filtre pour observer la vitesse des opportunités gagnantes fermées ou perdues clôturées.
