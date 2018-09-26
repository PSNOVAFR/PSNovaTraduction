[3]: https://github.com/Arks-Layer/PSO2JPTranslations/blob/master/resources/rightmeow.png

<p align="center">
  <img src="https://github.com/Arks-Layer/PSNovaTranslations/blob/master/resources/Phantasy-Star-Nova-Logo.png" alt="PS Nova Logo"/>
</p>

[Build status](https://travis-ci.org/PSNOVAFR/PSNovaTraduction.svg?branch=master)

# PSNova Traduction

Bienvenue dans le repertoir Github PSNova Traducions.

Ce dépôt est dédié à la traduction de textes de jeu PS: Nova du japonais vers le francais. Nous espérons que la publication de nos textes de jeu et l’ouverture de ce repertoir permettront aux ARKS non-japonais de profiter du jeu dans leur langue maternelle.

<i>Bien que nous apprécions les efforts de ceux qui ne parlent pas japonais (à travers Google traduction et similaires), nous aimerions que seuls ceux qui maîtrisent la langue japonaise soumettent des modifications à ces. ありがとう～ (*＾▽＾)／</i>

## Contributions

1. Cliquez sur le fichier que vous souhaitez modifier
2. Cliquez sur l'icône représentant un crayon
3. Modifier le fichier au contenu de votre choix !
4. Écrivez un bref résumé des modifications au bas de la page
5. Appuyez sur "Create a new branch for this commit and start a pull request." (<b>NE PAS ENREGISTRER DIRECTEMENT DANS MAITRE.</b>)
6. Votre demande de RP sera examinée et acceptée ou refusée.

## Processus d'édition

S'il vous plaît mettez votre traduction dans le champ "Texte" comme ça:
  
```
  "310040": {
    "OriginalText": "ポストアタック",
    "Text": "Post-attaque",
    "Enabled": false
  },
```

Ensuite, changez le false to true, donc ça finit comme ça:

```
  "310040": {
    "OriginalText": "ポストアタック",
    "Text": "Post-attaque",
    "Enabled": true
  },
```

S'il vous plaît noter qu'il peut y avoir des choses "bizarres" dans le texte! Par exemple, `\n`. Ceux-ci seront détaillés ci-dessous.


![3]

## Tu ne connais pas le japonais mais tu veux quand même contribuer ?

Si vous ne comprenez pas le japonais, mais que vous voulez quand même aider, vous pouvez regarder les lignes traduites et vous assurer que toute la grammaire et l'orthographe sont correctes..

## Tailles d'entrée

Voici une liste des tailles qu'une région accepte avant de commencer à redimensionner. Celles-ci doivent rester aussi proches que possible pour que le texte n'apparaisse pas trop petit à cause du redimensionnement automatique.

```
Affix Descriptions - 40 Characters, 4 Lines
Class Descriptions - 40 Characters, 4 Lines
Item Descriptions - 40 Characters, 4 Lines
Skill/GA/Technique Descriptions - 40 Characters, 4 Lines

Quest Names - 25 Characters
Loading Screen - 60 Characters, 2 Lines

Effects - 20 Characters
          15-18 Characters if it's a numeric effect to make room for the maximum potential number/percentage
```

## Système de message (RMD)

Voici quelques informations de base sur RMD, le format utilisé par le jeu pour stocker et gérer ses entrées de chaîne et sa table de chaînes.

### ID Ranges

Vous pouvez vous référer à NovaParse's [Export JSON](https://github.com/PSNOVAFR/Outils-NOVA/blob/master/NovaParse/Export.json) fichier pour une référence des plages d'ID RMD.

### Régions de texte

Nova's GUI utilise le concept de régions pour aligner et contenir des éléments d'interface utilisateur et de texte. Le système est suffisamment intelligent pour tenter d'ajuster automatiquement les contrôles à l'intérieur de sa région contenant. Cela peut être utilisé pour tenir dans de plus grandes quantités de texte que ce qui est immédiatement évident. N'oubliez pas qu'il n'y a pas de restriction à cette règle, il faut donc veiller à ne pas étirer le texte verticalement ou horizontalement au point où les glyphes individuels deviennent illisibles.

### Control Codes

Ces codes de contrôle sont utilisés pour faire diverses choses, comme changer la couleur du texte ou insérer des images..

#### Basic

```
\n - Newline
```

#### Ruby

Ruby est un code de contrôle spécial avec traitement spécial. Les codes de contrôle Ruby placent le texte spécifié sur le texte environnant. Ça commence par `[ruby ` et est ensuite procédé avec le texte à placer sur le dessus du texte environnant, puis une fermeture `]`. utilise `[/ruby]` fermer le bloc Ruby. Un exemple:

```
msg_100000010010013.rmd:
お願い……わたしの[ruby ほし]惑星[/ruby]を……助けて。
```

apparaîtra comme ca:

```
               ほし
お願い……わたしの惑星を……助けて。
```

#### Couleurs

Ces codes de contrôle changeront la couleur du texte environnant. Vous devez préfixer le texte que vous souhaitez colorer avec un code de contrôle de couleur, puis, après le texte, ajoutez le code de contrôle de fermeture de couleur.

```
[a 03] - Orange
[a 06] - Bleu
[a 07] - Jaune
[b] - Couleur Close
```

#### Variables

Il y a 4 codes de contrôle variables. La signification de ces variables changera en fonction du contexte du message qui les contient. Donc, <b>ils sont très spécifiques et ne devraient être utilisés que dans les messages appropriés pour éviter des problèmes potentiels dans le jeu !</b>

```
[e 00 00] - Variable 1
[e 01 00] - Variable 2
[e 02 00] - Variable 3
[e 03 00] - Variable 4
```

#### Images

Ces codes de contrôle peuvent être utilisés pour insérer des images de boutons et d’icônes dans le texte..

```
[f 01] - X
[f 02] - Circle
[f 03] - Square
[f 04] - Triangle
[f 07] - L
[f 08] - R
[f 09] - Start
[f 0a] - Select
[f 0b] - Left Thumbstick
[f 0c] - Right Thumbstick
[f 1b] - Circle
[f 1c] - X
[f 64] - PS Button
[f 66] - Right Thumbstick
[f 67] - Left Thumbstick
[f 68] - Left Thumbstick + X
[f 69] - Left Thumbstick + Triangle
[f 6a] - Left Thumbstick + Square
[f 6b] - Left Thumbstick + L
[f 6c] - Left Thumbstick + R
[f 6d] - L1
[f 6e] - R1
[f 6f] - L2
[f 70] - R2
[f 71] - L3
[f 72] - R3
[f 73] - Square
[f 74] - Triangle
[f 75] - X
[f 76] - Circle
[f 77] - Left Thumbstick + Circle
[f 78] - L
[f 79] - R
[f 7a] - D-Pad Left
[f 7b] - D-Pad Right
[f 7c] - D-Pad Up
[f 7d] - D-Pad Down
[f 7e] - Select
[f 7f] - Gran Icon
[f 80] - Unknown Icon
[f 9c] - Unknown Icon
```
