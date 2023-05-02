```typescript
type Route = { path: string; children?: Routes }

type Routes = Record<string, Route>

  

// Errors are highlighted
// Better autocomplete since it knows all the fields in the object
// satisfies work great with objects

const routes = {

AUTH: {

path: "/auth",

},

} satisfies Routes

  

// No Error Highlighted
// Won't autocomplete routes.AUTH.path
// Since the string type in Record<string, Route> is generic


// const routes : Routes = {

// AUTH: {

// path: "/auth",

// },

// }

// I think satisfies provide better typechecking and autocomplete because it passes through the object once, so it knows all the fields.

  

routes.AUTH.path // ✅

routes.AUTH.children // ❌ routes.auth has no property `children`

routes.NONSENSE.path // ❌ routes.NONSENSE doesn't exist
```