We can separate the client's data fetching into two broad categories:
**initial** and **on demand**.
We can use simple `fetch` instead of using data fetching libraries, but a lot of concerns we'd have to implement manually.
A *performant* app is always subjective and depends on the message we're trying to convey to the users.
When fetching data, especially initially, we need to be aware of browser limitations on parallel requests.
Waterfalls appear when we trigger data fetching not in parallel, but conditionally or in sequence.
We can use techniques such as `Promise.all`, parallel promises, or data providers with Context to avoid waterfalls.
We can pre-fetch critical resources even before React is initialized, but we need to remember browser limitations while doing so.

