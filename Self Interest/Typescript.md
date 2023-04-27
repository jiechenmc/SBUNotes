```typescript
type Route = { path: string; children?: Routes }

type Routes = Record<string, Route>

  

// Errors are highlighted

const routes = {

AUTH: {

path: "/auth",

},

} satisfies Routes

  

// No Error Highlighted

// const routes : Routes = {

// AUTH: {

// path: "/auth",

// },

// }

  

routes.AUTH.path // ✅

routes.AUTH.children // ❌ routes.auth has no property `children`

routes.NONSENSE.path // ❌ routes.NONSENSE doesn't exist
```