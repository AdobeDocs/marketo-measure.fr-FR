---
unique-page-id: 18874648
description: Différence entre une conversion de Google Analytics et une Buyer Touchpoint - [!DNL Marketo Measure]
title: Différence entre une conversion de Google Analytics et un point de contact acheteur
exl-id: d09d963c-3207-467c-852a-d1edd49511fa
feature: Touchpoints
source-git-commit: 4787f765348da71bc149c997470ce678ba498772
workflow-type: tm+mt
source-wordcount: '495'
ht-degree: 5%

---

# Différence entre une conversion de Google Analytics et un point de contact acheteur {#difference-between-a-google-analytics-conversion-and-a-buyer-touchpoint}

Découvrez ce qu’est un objectif [!DNL Google Analytics (GA)] et comment il se différencie d’un Buyer Touchpoint.

**Que sont les conversions de Google Analytics ?**

Les conversions [!UICONTROL Google Analytics] sont déterminées par la façon dont un marketeur ou un développeur web code les performances &quot;objectif&quot; sur un site web particulier. Les objectifs, selon Google, peuvent être considérés comme &quot;effectuer un achat (pour un site de commerce électronique), terminer un niveau de jeu (pour une application de jeu mobile) ou envoyer un formulaire d’information de contact (pour un site de marketing ou de génération de prospects)&quot;. La plupart du temps, les marketeurs voient les objectifs/conversions comme une personne remplissant un formulaire d’information.

Cependant, les objectifs ne peuvent pas être codés pour gérer un comportement spécifique. Il existe plutôt des types d’objectifs qu’un développeur web peut configurer. Voici quelques exemples :

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
   <td>Un emplacement spécifique charge</td> 
   <td><em>Merci de vous être inscrit !</em> page web ou écran d’application</td> 
  </tr> 
  <tr> 
   <td>Durée</td> 
   <td>Sessions qui durent une durée spécifique ou plus</td> 
   <td>10 minutes ou plus passées sur un site d’assistance</td> 
  </tr> 
  <tr> 
   <td>Pages/Screens par session</td> 
   <td>Un utilisateur affiche un nombre spécifique de pages ou d’écrans.</td> 
   <td>5 pages ou écrans ont été chargés</td> 
  </tr> 
  <tr> 
   <td>Événement</td> 
   <td>Une action définie comme un événement est déclenchée</td> 
   <td>Recommandations sociales, lecture vidéo, clic publicitaire</td> 
  </tr> 
 </tbody> 
</table>

La plupart des spécialistes du marketing configurent leurs conversions comme &quot;objectifs de destination&quot;, ce qui signifie qu’ils créent généralement une page de remerciement après un formulaire pour tenir compte d’une conversion formelle.

Cela signifie que Google considère les pages vues de remerciement comme une conversion. D’un point de vue Google Analytics, c’est une prise de conscience que la plupart des spécialistes du marketing sont d’accord.

Cependant, les points de contact d’achat agissent différemment.

**En quoi les points de contact de l’utilisateur diffèrent-ils ?**

[!DNL Marketo Measure] JavaScript effectue le suivi des données de session et des envois de formulaire sur tous les formulaires d’un site particulier. Il n’est pas nécessaire de coder les objectifs du point de vue [!DNL Marketo Measure]. Ce processus est automatique. Pour les envois de formulaire, [!DNL Marketo Measure] signale une remplissage de formulaire chaque fois qu’un utilisateur anonyme remplit des champs d’information sur un formulaire particulier et clique également sur le bouton d’envoi de formulaire. [!DNL Marketo Measure] n’a pas besoin d’une page de remerciement pour enregistrer l’envoi du formulaire.

[!DNL Marketo Measure] crée un point de contact de formulaire lorsque :

* Un prospect/contact associé à ces conversions apparaît dans votre CRM.
* Le fichier JS [!DNL Marketo Measure] est présent sur les pages web contenant le formulaire.
* Un formulaire est envoyé dans le cadre d’une session de 30 minutes.

[!DNL Marketo Measure] ignore les conversions Destination Google Analytics lorsque :

* Un robot envoie les formulaires sur un site web (ces robots ne sont généralement pas intégrés au CRM d’un client).
* Un utilisateur envoie davantage de formulaires après leur premier envoi. [!DNL Marketo Measure] poussera uniquement la première conversion de cette session.
* L’utilisateur clique plusieurs fois sur l’envoi du formulaire. [!DNL Marketo Measure] ne prendra en compte que la première soumission de formulaire.
* L’utilisateur recharge la page de remerciement plusieurs fois.
* L’utilisateur utilise n’importe quel outil de blocage des publicités.

Comme vous pouvez le constater, il existe des différences fondamentales entre ce que GA et [!DNL Marketo Measure] considèrent comme une conversion. Par conséquent, il est probable que le nombre de conversions et le nombre de points de contact du formulaire diffèrent.
