## 1. Structure de code

RAS

## 2. Liste

RAS

## 3. Details

RAS


## 4. Deck

RAS

## 5. Recherche

- Un petit bug sur le texte **Résultat de la recherche : NaN**. Ajouter un `+` devant un variable va le transformer en `number`, c'est comme écrire `parseInt(searchedElement)`.

```javascript
title: 'Résultat de la recherche : ' + (searchedElement === 'null' ? ' sans élément' : + searchedElement),
```

