# Journée de soudure – THT, SMD & Carte finale mixte

## 🛠️ Introduction

Ce projet consistait à souder trois cartes électroniques :  
1. Une première en **THT**,  
2. Une seconde dédiée à l’**entraînement SMD**,  
3. Une finale mêlant **THT et SMD**

J’ai réalisé l’intégralité du travail en une seule journée, alors que mon PCB final n’était même pas encore terminé sur KiCad. Cette journée a été un vrai marathon de soudure, mêlant efficacité, expérimentations, réussites… et galères inattendues.

---

## 🔧 Processus & Observations

### 1. Board d’entraînement SMD

Dès mon arrivée, on m’a directement donné la carte d’entraînement SMD (alors que je n’avais pas encore fait la THT).  
Ayant déjà soudé auparavant, je n’ai pas été choqué, surtout après la crash course de Baptiste qui nous a montré comment souder notre première résistance sur ma board.

- J’ai soudé une résistance et une LED pour me chauffer, puis le reste à la chaîne sans difficulté.
- Pour les deux IC, j’ai profité pour utiliser de la **pâte à souder + pistolet à air chaud**, une technique que j’avais déjà vue en vidéo mais jamais testée.
- Les deux IC ont été réussis du premier coup, et j’ai même pu montrer la technique à mes camarades.
- Le reste des composants (résistances, condensateurs) a été soudé sans problème.

#### Tests

- L’Arduino du bout de la table m’a permis de valider la carte THT : toutes les LEDs clignotaient comme prévu.

---

### 2. Board THT

Cette carte n’avait pas été expliquée au préalable.  
Après un tutoriel YouTube de 20 secondes pour le THT, j’ai décidé de procéder du plus petit au plus grand :

1. Résistances  
2. Quartz  
3. Condensateurs  
4. LEDs  
5. Pin headers  

J’ai utilisé l’Omnifixo pour maintenir la carte à plat afin d’éviter les mouvements pendant la soudure.

#### Difficultés rencontrées

- Une première rangée de pins soudée de travers, que j’ai trop tenté de corriger avant d’abandonner (difficile de desouder une fois tous les pins soudés, je n'ai pas pensé a l'air chaud a ce moment la).
- Méthode améliorée : tenir les pins droits à la main pour les extrémités avant de souder le reste.
- Sur la carte suivante : insérer tous les headers d’un coup avant de souder pour les maintenir tous droits et souder uniquement les extremités avant de verifier et continuer.

#### Tests

- Leds verte et rouge que j'avais soudé dans le mauvais ordre par mégarde avant de verifier dans quel ordre elles devaient vraiment aller!

---

### 3. Board finale (mixte SMD + THT)

C’est sur cette carte que les galères ont commencé.

#### Première tentative

- IC soudé avec pâte + air chaud, mais avec **trop de pâte** :  
  → nettoyage au solder wick 
  → drag soldering pour homogénéiser les pads qui n'avaient plus assez d'étain et ceux qui en avaient encore trop 
- Après avoir soudé tous les composants : **court-circuit entre 5V et GND**.  
- Aucun bridge visible. IC retiré entièrement → toujours le court-circuit.  
- Dessoudage de condensateurs, inspection… jusqu’à trouver un fragment d’étain ayant abîmé le vernis.  
- Je commence à suspecter un PCB défectueux → nouvelle carte.

#### Deuxième tentative

- IC soudé au fer en drag soldering.  
- Test avant les pins : **même court-circuit**.  
- Deux zones du PCB semblaient abîmées → abandon de cette carte aussi.

#### Troisième tentative

Cette fois, plus de risques :

- Tous les pads recouverts de pâte à souder.
- Tous les composants placés en 15 minutes.
- Air chaud 30–45 s → parfait.
- Ajustements à la pince, nettoyage : carte impeccable.

… mais toujours aucun fonctionnement.

C’est en aidant une amie que je découvre finalement que :  
**la LED rouge était inversée** sur TOUTES mes versions.

- Je retire la LED a l'air chaud .  
- Je la soude dans la BONNE orientation .  
- Test : **la carte fonctionne enfin**.

Il était minuit passé, j’ai soudé les derniers pins en speedrun, rangé mon poste et pris les derniers métros.  
En écrivant ce README à 3h du matin, dans mon lit, je me rends compte que… j’ai oublié un pin THT _(je sors donc mon fer a souder...)_.

---

## ⚠️ Difficultés & Solutions

| Difficulté | Solution |
|------------|----------|
| Pins tordus sur la carte THT | placer tous les pins, ça se tient droit presque seul |
| Surplus de pâte / bridges | Solder wick + drag soldering + flux |
| Court-circuit 5V–GND | Dessoudage complet, inspection, changement de carte |
| PCB abîmé | Recommencer sur une nouvelle carte |
| Orientation des LEDs | Vérification sur la carte d'exemple (cause finale du problème) |
| Pin manquant | Retour au fer à souder à 3 h du matin 💀 |

---

## ✅ Conclusion

Cette journée a été intense mais extrêmement formatrice :

- maîtrise du drag soldering,  
- utilisation de la pâte à souder et de l’air chaud,  
- debugging réel de problèmes électroniques, (mieux faire attention aux BOM pour les orientations)
- organisation efficace pour SMD et THT.

Malgré les multiples galères, j’ai obtenu au final une carte parfaitement fonctionnelle — et beaucoup d’expérience.

