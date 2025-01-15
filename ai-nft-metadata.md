# Métadonnées AI-NFT

Créer des AI-NFT est similaire à la création d'un NFT traditionnel, **avec** un champ supplémentaire `ai_agent` qui décrit la configuration d'un agent IA et le moteur qu'il utilise, stocké dans les métadonnées.

## Moteur IA pris en charge <a href="#metadata-json" id="metadata-json"></a>

<table><thead><tr><th width="224">Moteur</th><th width="231">Nom du moteur</th><th>Fichier de caractère</th></tr></thead><tbody><tr><td><a href="https://github.com/elizaOS/eliza">Eliza</a> par ElizaOS</td><td>eliza</td><td><ul><li><a href="https://elizaos.github.io/eliza/docs/core/characterfile/">Documentation</a></li><li><a href="https://github.com/elizaOS/characterfile">Template</a></li><li><a href="https://github.com/elizaOS/eliza/tree/main/characters">Exemple</a></li></ul></td></tr></tbody></table>

## Métadonnées AI-NFT JSON <a href="#metadata-json" id="metadata-json"></a>

| Champ                        | Type   | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| ---------------------------- | ------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **ai\_agent** (ajouté récemment)  | objet  | <p>La configuration qui définit l'agent IA associé à ce NFT. </p><ul><li><strong>engine</strong> (string) : le moteur utilisé pour faire fonctionner l'agent IA. Par défaut "eliza".</li><li><strong>character</strong> (objet) : le fichier de caractère JSON qui décrit un agent IA. Consultez <a href="https://github.com/elizaOS/characterfile?tab=readme-ov-file">ici</a>.</li></ul>                                                                                                                                                                                     |
| **name**                     | chaîne de caractères | Nom de l'actif.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| **description**              | chaîne de caractères | Description de l'actif.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| **image**                    | chaîne de caractères | URI pointant vers le logo de l'actif.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| **animation\_url**           | chaîne de caractères | URI pointant vers l'animation de l'actif.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| **external\_url**            | chaîne de caractères | URI pointant vers une URL externe définissant l'actif — par exemple, le site principal du jeu.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| **attributes**               | tableau | <p>Tableau d'attributs définissant les caractéristiques de l'actif.</p><ul><li><strong>trait_type</strong> (string) : Le type d'attribut.</li><li><strong>value</strong> (string) : La valeur de cet attribut.</li></ul>                                                                                                                                                                                                                                                                                                                                        |
| **properties**               | objet  | <p>Propriétés supplémentaires définissant l'actif.</p><ul><li><p><strong>files</strong> (tableau) : Fichiers supplémentaires à inclure avec l'actif.</p><ul><li><strong>uri</strong> (chaîne de caractères) : URI du fichier.</li><li><strong>type</strong> (chaîne de caractères) : Le type du fichier. Par exemple, <code>image/png</code>, <code>video/mp4</code>, etc.</li><li><strong>cdn</strong> (booléen, optionnel) : Indique si le fichier est servi depuis un CDN.</li></ul></li><li><strong>category</strong> (chaîne de caractères) : Une catégorie média pour l'actif. Par exemple, <code>video</code>, <code>image</code>, etc.</li></ul> |

## Exemple

```json
{
  // Champ agent IA
  ai_agent: {
    engine: "eliza",
    character: {
      // nom de l'agent
      name:"eliza",
      // déclarations de fond
      bio: [
        "Les lignes bio sont de courts extraits qui peuvent être composés ensemble dans un ordre aléatoire.",
        "Nous avons constaté qu'il augmente l'entropie de randomiser et de sélectionner uniquement une partie de la bio pour chaque contexte.",
        "Cette 'entropie' sert à élargir la distribution des sorties possibles, ce qui devrait donner des réponses plus variées mais continuellement pertinentes."
      ],
      lore: [
        "Les lignes de lore sont de courts extraits qui peuvent être composés ensemble dans un ordre aléatoire, tout comme la bio",
        "Cependant, celles-ci sont généralement plus factuelles ou historiques et moins biographiques que les lignes biographiques",
        "Les lignes de lore peuvent être extraites des journaux de chat et des tweets comme des choses que le personnage ou ce qui leur est arrivé",
        "Lore devrait également être randomisé et échantillonné pour augmenter l'entropie dans le contexte"
        ],
      ... //xxx.character.json de https://github.com/elizaOS/eliza/tree/main/characters
    }
  },
  // Métadonnées NFT standard
  name: 'Mon NFT',
  description: 'Ceci est un NFT sur Solana',
  image: imageUri[0],
  external_url: 'https://example.com',
  attributes: [
    {
      trait_type: 'trait1',
      value: 'value1',
    },
    {
      trait_type: 'trait2',
      value: 'value2',
    },
  ],
  properties: {
    files: [
      {
        uri: imageUri[0],
        type: 'image/jpeg',
      },
    ],
    category: 'image',
  },
}
