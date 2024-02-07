## Definition

Using Server Components to fetch data
By default, Next.js applications use React Server Components.
Fetching data with Server Components is a relatively new approach and there are a few benefits of using them:

Server Components support promises, providing a simpler solution for asynchronous tasks like data fetching. You can use async/await syntax without reaching out for useEffect, useState or data fetching libraries.
Server Components execute on the server, so you can keep expensive data fetches and logic on the server and only send the result to the client.
As mentioned before, since Server Components execute on the server, you can query the database directly without an additional API layer.
