## 1. Structure de code

RAS

## 2. Liste

RAS

## 3. Details

- Les informations sont bien afficher.
- Par contre, la gestion de l'erreur 404 n'est pas gérer. Il faudrait ajouter une exception après la recherche en base de donnée, si l'éléments n'existe pas, on retourne une page 404.

```javascript
...

const id = Number(req.params.id);
try {
    const card = await dataMapper.getOneCard(id);
    if (!card) {
        res.render('notFound');
        return;
    }
    res.render('card', { card });
} catch (error) {
    console.error(error);
    res.status(500).send(`An error occured with the database :\n${error.message}`);
}

...
```
- La page détails ne detecte pas si l'élément est déjà dans le deck. Donc, on ne peut pas l'enlever du deck. Le mieux est de donner les information du deck depuis le session vers la page de vue du détails pour gérer ce cas.


## 4. Deck

- Aucun moyen d'enlever un élément du deck, il faudrait ajouter un bouton qui permetterai de le faire. Ajouter un nouveau controller qui éfface un élément du deck.
- Il serait mieux aussi d'ajouter un lien vers le détails d'une carte. Là, les éléments sont non cliquable.
- La limite de nombre de deck n'est pas encore géré

## 5. Recherche

- Afficher juste le nom dans les résultats ne rends pas la fonctionnalité usable. Il manque trops peut d'information. Le mieux, c'est de réutiliser la vue déjà utiliser depuis la pages d'accueil.
- Seule la recherche par "élément" qui existe. Les autres controller ne sont pas encore créé.
- Côté code, faire une filtre côté javascript n'est pas optimisé. Le mieux, c'est de faire une [filtre sur la requette en base de donnée](https://www.w3schools.com/sql/sql_where.asp).

