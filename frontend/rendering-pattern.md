## static rendering or static site generation (SSG)

Static Site Generation (SSG) does the rendering at build time instead of request time, so the server does not need to do any additional rendering and requests can be processed very quickly. The process for the client hydrating and bootstrapping is the same, however.

## dynamic rendering or Server Side Rendering (SSR)

Server Side Rendering (SSR) is the process of rendering content to a client based on an HTTP request. A client makes a request and the server processes it, returning rendered HTML back to the client. The Client then hydrates that HTML and bootstraps the client-side JS app.
