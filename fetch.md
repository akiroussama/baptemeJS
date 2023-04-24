Pour expliquer la notion de `fetch` simplement, il faut comprendre certaine concepte de base.

## 1. AJAX

AJAX ou Async Javascript XML est un notion introduite sur javascript pour éviter de toujour recharger la page à chaque intéraction. Cela rend l'interaction plus fluide.

![Javascript AJAX](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTDRy3sah8B8J_FmTWtTXk37FrHpW0jA5xKlg&usqp=CAU)

Pour obtenir ces données depuis le serveur, bloquer la page rends l'expérience d'utilisation impossible, ce qui introduit une nouvelle notion, l'asynchrone.
Cela permet à l'éxecution de continuer en attendant la réponse venant du serveur.
Les meilleurs moyen de gérer l'asynchrone sur javascript sont :

- [Les callback](https://www.w3schools.com/js/js_callback.asp)
- [Les Promise](https://www.w3schools.com/js/js_promise.asp)

Pour envoyer une requette, on peut utiliser l'objet [XMLHttpRequest](https://www.w3schools.com/js/js_ajax_http.asp), qui, on ne vas pas se mentir, a besoin de beaucoup de code pour envoyer une seule requette 😜. Cette approche et utiliser avec les callback. <br/>

Une autre alternative est [fetch](https://www.w3schools.com/jsref/api_fetch.asp), qui permet de façon plus abstraite, d'envoyer une requette http. Cette approche est utilisé avec les Promise.

## 2. Promise

Les Promise, pour être simple, c'est un objet qui execute un action asynchrone, avec une promesse de réponse (c'est à dire, pas tout de suite).<br>
Une Promise à trois états :

- Pending : L'action est en cours
- Resolved : La promesse est résolu
- Rejected : La promesse est rejeté

Une Promise est résolu quand l'action c'est bien passé. A contrario, une Promise est rejeté si il y a eu une erreur dans l'éxecution.

## 3. fetch

Donc, `fetch` est un moyen de récupérer des données venant d'un serveur de manière asynchrone avec un Promise en retour.

```javascript
const request = fetch(`https://example.com/data`)
// Faire une action si la requette est en succès
request.then((data) => console.log(data))
// Faire quelque chose si la requette tombe en erreur
request.catch((error) => console.log(error))

```

Ou écrit plus simplement :

```javascript
fetch(`https://example.com/data`)
    .then((data) => console.log(data)) // Faire une action si la requette est en succès
    .catch((error) => console.log(error)) // Faire quelque chose si la requette tombe en erreur
```

Ou écrit beaucoup plus simplement avec [async await](https://www.w3schools.com/js/js_async.asp)

```javascript
const getData = async () => {
    try {
        const data = await fetch(`https://example.com/data`)
        // Faire une action si la requette est en succès
        return data
    } catch(e) {
        // Faire quelque chose si la requette tombe en erreur
        throw e
    }
}

getData()
```

