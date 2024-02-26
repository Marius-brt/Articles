Evnts est une librairie qui permet de changer le state d'un hook React à travers différents components ou script natif de manière réactif. Ce package permet également la persistance des données dans le localstorage par exemple. 

Prenons un exemple concret, dans un projet j'avais besoin d'afficher une banière d'erreur lorsque que la connexion à la base de donnée est impossible. Voici comment j'ai procédé :

`onlineEvent.ts`
```ts
import {createEvent} from '@marius.brt/evnts';

export const onlineEvent = createEvent('onlineEvent', true);
```

`database.ts`
```ts
...

export const execute = async(collection: string) => {
  try {
    ... execute
    onlineEvent.setValue(true)
  } catch(e) {
    onlineEvent.setValue(false)
  }
}
```

`App.tsx`
```tsx
export default function App() {
  return <>
    <ToggleEvnt event={onlineEvent}>
        <p>Offline!</p>
    </ToggleEvnt>
    ...
  </>
}
```
