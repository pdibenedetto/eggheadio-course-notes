# Separate API Utility Functions from React Components

**[📹 Video](https://egghead.io/lessons/react-separate-api-utility-functions-from-react-components)**

👍 It's a good practice to separate concerns to improve code re-usability, like moving helpers functions or API functions to a shared place where other components can use it. In this example we do a call to `fetch` and to a particular url endpoint to retrieve one particular pokemon, and that is not very interesting nor flexible, this can be extracted to an API function allowing this logic to be dynamic.

To do this we just require to create a new function that will hold the fetch logic. Will receive as an argument an id.

```javascript
function fetchPokemon(id) {
  return fetch(`https://pokeapi.co/api/v2/pokemon/${id}`).then(res => res.json());
}
```

and then just call this function in the component.

👍 Another good practice is to move all the related code, like in this example the API code, to it's own file or folder. In this example a new file is created called `api.js` this file will hold all of the api related code, **one responsability**.



``` javascript
export function suspensify(promise) {
  let status = "pending";
  let result;
  let suspender = promise.then(
    response => {
      status = "success";
      result = response;
    },
    error => {
      status = "error";
      result = error;
    }
  );

  return {
    read() {
      if (status === "pending") {
        throw suspender;
      }
      if (status === "error") {
        throw result;
      }
      if (status === "success") {
        return result;
      }
    }
  };
}

export function fetchPokemon(id) {
  return fetch(`https://pokeapi.co/api/v2/pokemon/${id}`).then(res => res.json());
}
```

Do not forget to export both functions to allow them to be imported by name inside the component file.

```javascript
import { fetchPokemon, suspensify } from "./api";
```



🔑 So to keep in mind. While you are developing and the application grows keep theis boundaries between componentes and API's or helpers. This will help with the future maintenance and readability of the application.

---

📹 [Go to Previous Lesson](https://egghead.io/lessons/react-wrap-fetch-requests-to-communicate-pending-error-and-success-status-to-react-suspense)
📹 [Go to Next Lesson](https://egghead.io/lessons/react-track-async-requests-with-react-s-usestate-hook)
