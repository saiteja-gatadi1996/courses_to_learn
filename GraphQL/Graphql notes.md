### What is Graphql?

- A query language for your API
- And a runtime for fullfulling those queries with your exisiting data.
- GraphQL provides a complete and understandable description of the data in your API
- The power to ask for exactly what they need and nothing more.
- Makes it easier to evolve API's over time, and enables powerful developer tools.

#### Problems with REST API
- Too much data will be loaded at the client side,
- If you want to fetch two different resources, you need to make two different calls to the server, whereas GraphQL let's you to get many resources in a single request.


#### Advantages of GraphQL:

- Describe what's possible with a type system 
- GraphQL API's are organized in terms of types and fields (not endpoints)
- Access the full capabilities of your data from a single endpoint.
- Uses types to ensure apps only ask what's possible and provide clear and helpful errors. 
- Apps can use types to avoid writing manual parsing code.
![image](https://github.com/saiteja-gatadi1996/notes/assets/42731246/fe9f8ecf-ee67-4835-804d-5da49611d665)
- Evolve your API without versions(you can modify your API over time without breaking backwards compatability)
- Also GraphQL provides a way to deprecate fields 
- You can add GraphQL to your existing applications.(No need to re-write your entire codebase).

```js
GraphQL provides the API layer whereas your data and logic can stay same.
``` 