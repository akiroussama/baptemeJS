## 1. Structure de code

### 1.1 mainControler.js

- Devrait juste contenir la page d'acceuil
- Avoir la page de détails d'une card sort la fonctionnalité de son contexte. Le mieux est de créer une nouvelle controller pour ça

## 2. Liste

- Affichage d'une carte non optimisé. Il faudrait suivre au minimum le [sémantic HTML](https://www.w3schools.com/html/html5_semantic_elements.asp). Distinger d'un élément block à un élément inline pour au moin position les éléments sans utiliser CSS.
- Le bouton censé être pour l'ajout dans le deck est ré-utilisé pour la page détails. Ca rend l'utilisation confu.

## 3. Details

- Buggé.
- Il faut éviter de nommer les variables `oneCard`, on s'y perds facilement ensuite. Soit, c'est `card` si c'est un seul élément, soit `cards` si c'est plusieurs éléments. Comme ça on ne s'y perd pas
- La page not found n'est pas câblé avec la page détails. Ce n'est pas encore fonctionnel. Le mieux, c'est de gérer l'abscence de l'élément et renvoyer la page 404 en conséquence

```javascript
...
try {
    const id = Number(request.params.id);

    const oneCard = await dataMapper.getCard(id);
    if (!card) {
        response.render('notFound');
        return;
    }
    response.render('main/cardDetails', {oneCard});
    
} catch (error) {
    console.log(error);
    response.status(500).send('Oups, nous rencontrons un problème technique');
}   
...
```


## 4. Deck

- Non implémenté.

## 5. Recherche

- Non fonctionnel
- `dataMapper` n'est importé nulle part.
- `dataMapper.cardElement` n'existe pas.
- `dataMapper.getCardByElement` ne reçoit pas l'éléments comme paramètre, ce qui figera le résultat retourné par le fonction.
