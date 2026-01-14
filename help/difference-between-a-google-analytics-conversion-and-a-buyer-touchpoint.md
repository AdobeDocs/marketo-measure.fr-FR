---
description: Différence entre une conversion Google Analytics et des conseils Buyer Touchpoint pour les utilisateurs de Marketo Measure
title: Différence entre une conversion de Google Analytics et un point de contact acheteur
exl-id: d09d963c-3207-467c-852a-d1edd49511fa
feature: Touchpoints
source-git-commit: fcd8e276c85669ddf12bd7404fb12d3e99b2642a
workflow-type: tm+mt
source-wordcount: '500'
ht-degree: 5%

---

# Différence entre une conversion de Google Analytics et un point de contact acheteur {#difference-between-a-google-analytics-conversion-and-a-buyer-touchpoint}

Découvrez ce qu’est un objectif [!DNL Google Analytics (GA)] et en quoi il se différencie d’un Buyer Touchpoint.

**Quelles sont les conversions de Google Analytics ?**

Les conversions [!UICONTROL Google Analytics] sont déterminées par la manière dont un spécialiste marketing ou un développeur web code l’achèvement de l’« objectif » sur un site web particulier. Selon Google, les objectifs peuvent être considérés comme « effectuer un achat (pour un site d’e-commerce), remplir un niveau de jeu (pour une application de jeu mobile) ou envoyer un formulaire de coordonnées (pour un site de marketing ou de génération de pistes) ». La plupart du temps, les professionnels du marketing perçoivent les objectifs/conversions comme quelqu’un qui remplit un formulaire d’information.

Cependant, les objectifs ne peuvent pas être codés pour gérer un comportement spécifique. Il existe plutôt des types d’objectifs qu’un développeur web peut configurer. Voici quelques-uns de ces exemples :

<table>
 <colgroup>
  <col>
  <col>
  <col>
 </colgroup>
 <tbody>
  <tr>
   <td><strong>Type d’objectif</strong></td>
   <td><p><strong>Description</strong></p></td>
   <td><strong>Exemple</strong></td>
  </tr>
  <tr>
   <td><p>Destination</p></td>
   <td>Un emplacement spécifique se charge</td>
   <td><em> Merci de vous être inscrit !</em> page web ou écran de l’application</td>
  </tr>
  <tr>
   <td>Durée</td>
   <td>Sessions d’une durée spécifique ou plus longue</td>
   <td>10 minutes ou plus passées sur un site d’assistance</td>
  </tr>
  <tr>
   <td>Pages/Screens par session</td>
   <td>Un utilisateur ou une utilisatrice consulte un nombre spécifique de pages ou d’écrans</td>
   <td>5 pages ou écrans ont été chargés</td>
  </tr>
  <tr>
   <td>Événement</td>
   <td>Une action définie comme un événement est déclenchée</td>
   <td>Recommandations par les réseaux sociaux, lecture vidéo et clic</td>
  </tr>
 </tbody>
</table>

La plupart des professionnels du marketing configurent leurs conversions en tant qu’« objectifs de destination », ce qui signifie qu’ils créent généralement une page de remerciement après un formulaire pour considérer qu’il s’agit d’une conversion formelle.

Cela signifie que Google considère les pages vues de remerciement comme une conversion. Du point de vue de Google Analytics, il s’agit d’une prise de conscience avec laquelle la plupart des spécialistes marketing sont d’accord.

Cependant, les points de contact de l’acheteur agissent différemment.

**En quoi les points de contact de l’acheteur diffèrent-ils ?**

[!DNL Marketo Measure] JavaScript effectue le suivi des données de session et des envois de formulaires sur tous les formulaires d’un site particulier. Il n’est pas nécessaire de coder les objectifs du point de vue [!DNL Marketo Measure]. Ce processus est automatique. Pour les envois de formulaire, [!DNL Marketo Measure] signale une saisie semi-automatique du formulaire chaque fois qu’un utilisateur anonyme remplit les champs d’information d’un formulaire particulier et clique également sur le bouton d’envoi du formulaire. [!DNL Marketo Measure] n’a pas besoin d’une page de remerciement pour enregistrer l’envoi du formulaire.

[!DNL Marketo Measure] crée un point de contact de formulaire lorsque :

* Un prospect/contact associé à ces conversions apparaît dans votre CRM.
* Le JS [!DNL Marketo Measure] est présent sur les pages web contenant le formulaire.
* Un formulaire est envoyé dans un délai de 30 minutes.

[!DNL Marketo Measure] ignore les conversions Analytics de Destination Google lorsque :

* Un robot envoie des formulaires sur un site web (ces robots n’arrivent généralement pas dans le CRM d’un client).
* Un utilisateur envoie d’autres formulaires après son premier envoi. [!DNL Marketo Measure] n’envoie que la première conversion à partir de cette session.
* L’utilisateur clique plusieurs fois sur l’envoi du formulaire. [!DNL Marketo Measure] ne prendra en compte que la première soumission de formulaire.
* L’utilisateur recharge la page de remerciement plusieurs fois.
* L’utilisateur utilise n’importe quel outil de blocage des publicités.

Comme vous pouvez le constater, il existe des différences fondamentales entre ce que GA et [!DNL Marketo Measure] considèrent comme une conversion. Par conséquent, il est probable que le nombre de conversions et le nombre de points de contact de formulaire diffèrent.
