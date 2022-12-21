---
unique-page-id: 18874682
description: Canaux et sous-canaux marketing - [!DNL Marketo Measure] - Documentation du produit
title: Canaux marketing et sous-canaux
exl-id: fbe2a994-cf6d-439c-af96-a562216434cc
source-git-commit: 02f686645e942089df92800d8d14c76215ae558f
workflow-type: tm+mt
source-wordcount: '472'
ht-degree: 4%

---

# Canaux marketing et sous-canaux {#marketing-channels-and-subchannels}

## But {#purpose}

Pour définir dans quel canal et sous-canal se trouvent [!DNL Marketo Measure], la manière dont ils sont associés à votre contenu, la différence entre les deux classifications et la manière dont ils sont utilisés au sein de la variable [!DNL Marketo Measure] application.

## APERÇU {#overview}

Les canaux marketing permettent de classer (ou de &quot;regrouper&quot;) vos activités marketing afin de faciliter la création de rapports, à la fois dans la variable [!DNL Marketo Measure] Dash de retour sur investissement ainsi que dans votre CRM. [!DNL Marketo Measure] s’accompagne de 12 canaux prêts à l’emploi (que vous pouvez personnaliser/renommer pour les adapter aux conventions de votre entreprise), ainsi que de la possibilité de créer d’autres canaux personnalisés pour un filtrage encore plus granulaire.

Chaque fois que vous recevez un visiteur sur l’une de vos pages de contenu de votre site (qu’il s’agisse d’une page web, d’un téléchargement de livre blanc, d’une URL de page, etc.), ce prospect est &quot;regroupé&quot; dans un canal/sous-canal en fonction de plusieurs paramètres de la gestion dynamique des balises trouvés dans l’URL :

* Moyen
* Source
* Campagne
* Page de destination
* Site Web de renvoi

Pour personnaliser le &quot;regroupement&quot; de vos pistes en fonction de leurs paramètres UTM, vous pouvez utiliser des règles de canal. Pour plus d’informations sur la configuration et la maintenance des règles de canal, [cliquez ici](/help/channel-tracking-and-setup/online-channels/online-custom-channel-setup.md).

Découvrez comment configurer votre [Canaux en ligne](/help/channel-tracking-and-setup/online-channels/online-custom-channel-setup.md) et [Canaux hors ligne](/help/channel-tracking-and-setup/offline-channels/offline-custom-channel-setup.md), ainsi que la différence entre eux.

**Canal marketing**

Le canal marketing est le niveau de classification le plus large et peut couvrir un large éventail de sous-canaux. Vous pouvez considérer ces sous-canaux comme le &quot;type&quot; de vos pistes. Exemples de canaux marketing : **Recherche payante, Recherche organique, Affichage,** et **Social payant**. Le canal marketing correspond généralement à la valeur du paramètre utm_medium qui se trouve dans votre URL.

**Sous-canal**

Les sous-canaux sont la deuxième pièce du puzzle lors du regroupement de vos pistes entrantes. Les sous-canaux racontent exactement l’histoire de _which_ L’itération de votre canal marketing a été utilisée. Par exemple, dans le canal de marketing social payant, vous pouvez disposer de sous-canaux pour **AdWords**, **BingAds**, **Facebook**, etc. Le Subchannel correspond généralement à la valeur du paramètre utm_source trouvée dans votre URL.

## Exemple de cas d’utilisation {#use-case-example}

Le diagramme ci-dessous illustre un exemple de canal marketing, de sous-canal et de contenu basé sur une page web avec l’URL suivante :

* [http://info.bizible.com/intro-guide-b2b-marketing-attribution?utm_source=linkedin&amp;utm_medium=paidsocial](http://info.bizible.com/intro-guide-b2b-marketing-attribution?utm_source=linkedin&amp;utm_medium=paidsocial)*

Dans ce cas, le contenu auquel l’utilisateur tente d’accéder est le Guide d’introduction à l’attribution marketing B2B. [!DNL Marketo Measure] analysera l’URL qui mène à ce contenu à l’aide des règles de canal configurées dans cette organisation et les utilisera pour &quot;regrouper&quot; cette piste dans le canal marketing &quot;Social payant&quot; et le sous-canal &quot;LinkedIn&quot;.

![](assets/1.jpg)

D&#39;autres exemples...

**Canal marketing (moyen)**

* PPC
* Social payant
* Social organique
* Adresse e-mail
* Événements et conférences
* Recherche/SEO organiques
* Presse
* Programmes de parrainage

**Sous-canal (source du point de contact)**

* Google AdWords
* BingAds
* Publicités Facebook
* Adroll
* Double-cliquer
* Capterra
* Campagnes de secours
* Publicités linkedIn

**Contenu (livres blancs, URL de page, billets de blog)**

* www.adobe.com/blog1
* www.adobe.com/whitepaper
* www.adobe.com/sign-up-now
