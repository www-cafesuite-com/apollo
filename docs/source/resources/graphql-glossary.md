---
title: GraphQL Glossary
description: A comprehensive list of important GraphQL words and acronyms
---


When you start diving into the GraphQL ecosystem, you'll probably encounter some unfamiliar terms and phrases along the way. To help you on your journey, we've defined some of the most common GraphQL vocabulary here in this handy cheat sheet.


<h2 id="Apollo">Apollo</h2>
<p>An open-source implementation of GraphQL that helps you manage data between the cloud and your UI. The Apollo platform is pluggable into your existing architecture and features production-ready tooling across the stack ([Server](https://www.apollographql.com/docs/apollo-server/getting-started.html), [Client](https://www.apollographql.com/docs/react/), and [Engine](https://www.apollographql.com/docs/engine/)).</p>

<h2 id="automatic-persisted-queries">Automatic Persisted Queries (APQ) </h2>
<p> A technique for improving GraphQL network performance with zero build-time configuration by reducing request size over the wire. A smaller signature reduces bandwidth utilization and speeds up client loading times. Apollo Server allows implementation of [Automatic Persisted Queries (APQ)](https://www.apollographql.com/docs/guides/performance.html#automatic-persisted-queries). </p>

<h2 id="argument">Argument</h2>
<p>A set of key-value pairs attached to a specific field. Arguments can be literal values or variables.</p>

```js
{
  human(id: "200") {
    weight(unit: "pounds")
    height
  }
}
```

<h2 id="alias">Alias</h2>
<p>An alternative name given to the result of a field to avoid conflicts during data fetching.</p>

```js
{
  admin: users(role: admin) {
    id
    firstname
    lastname
  }
  managers: users(role: manager) {
    id
    firstname
    lastname
  }
}
```

<h2 id="data-source">Data Source</h2>
<p>A class that encapsulates fetching data from a particular service, with built-in support for caching, deduplication, and error handling.</p>

<h2 id="deferred-query">Deferred query</h2>
<p>A declaration prefixed with an @ character that encapsulates programming logic for query execution on the client or server. There are built-in such as @skip, @include and custom directives. It can be used for features such as authentication, incremental data loading, etc.</p>

<h2 id="directive">Directive</h2>
<p>A declaration prefixed with an @ character that encapsulates programming logic for query execution on the client or server. There are built-in such as @skip, @include and custom directives. It can be used for features such as authentication, incremental data loading, etc.</p>

<h2 id="docstring">Docstring</h2>
<p>It is used for providing descriptions of types, fields and arguments. It adds metadata to a GraphQL document. Docstrings show up in the documentation panel inside GraphQL playground and GraphiQL.</p>

```js
"""
Description for the User
"""
type User {
  """
  Description for first Name
  """
  firstName: String!

  age(
    """
    Must be an integer
    """
    arg: Int
  )
}
```

<h2 id="document">Document</h2>
<p>A file or request string that contains one or multiple definitions of a GraphQL type system and can be interpreted by a GraphQL execution engine.</p>

<h2 id="extensions">Extensions</h2>
<p>Special fields in the Graphql response that allows you to attach extra metadata. [Apollo tracing](https://github.com/apollographql/apollo-server/tree/master/packages/apollo-tracing) is an example of an extension. </p>


<h2 id="field">Field</h2>
<p>A unit of data you are asking for in a Schema, which ends up as a field in your JSON response data.</p>

```js
type Author {
  id: Int!
  firstName: String
  lastName: String
}
```

`id`, `firstName`, and `lastName` are fields in the example above.


<h2 id="fragment">Fragment</h2>
<p>A selection set that can be reused in multiple query operations. A [GraphQL fragment](https://www.apollographql.com/docs/react/advanced/fragments.html) is a shared piece of query logic.</p>

```js
fragment UserData on User {
  id: ID!
  firstName: String!
  lastName: String!
}

query getUsers {
  allUsers {
    ...UserData
  }
}
```

<h2 id="gql-function">gql function</h2>
<p>A [JavaScript template literal tag](https://github.com/apollographql/graphql-tag) that parses GraphQL queries into an abstract syntax tree (AST).</p>

```js
const typeDefs = gql`
  type File {
    filename: String!
    mimetype: String!
    encoding: String!
  }
`;
```

<h2 id="graphql-playground">GraphQL Playground</h2>
<p>An in-browser IDE for GraphQL development and workflow. Added benefits exist such as theme change, automatic schema reloading, HTTP headers configuration, query history and GraphQL subscription support. In addition, it comes [out-of-the-box in Apollo Server 2](https://www.apollographql.com/docs/apollo-server/features/graphql-playground.html).</p>

<h2 id="graphiql">GraphiQL</h2>
<p>An in-browser IDE for GraphQL development.</p>

<h2 id="introspection">Introspection</h2>
<p>A technique to provide detailed information about a GraphQL API's schema. Types and fields used in introspection are prefixed with "__" two underscores.</p>

<h2 id="mutation">Mutation</h2>
<p>An operation for creating, modifying and destroying data.</p>

```js
mutation AddTodo($type: String!) {
  addTodo(type: $type) {
    id
    type
  }
}
```

<h2 id="normalization">Normalization</h2>
<p>A technique for transforming default GraphQL responses into a specific desired format.</p>

```js
// Example of a default GraphQL response
const response = {
  data: {
    getUser: {
      __typename: 'User',
      uid: '5a6efb94b0e8c36f99fba013',
      email: 'john.doe@yahoo.com',
    },
  },
}

// After Normalization
{
 users: {
    '5a6efb94b0e8c36f99fba013': {
      uid: '5a6efb94b0e8c36f99fba013',
      email: 'john.doe@yahoo.com'
   }
 }
}
```

<h2 id="object-type">Object Type</h2>
<p>A type in a GraphQL schema which has fields.</p>

```js
type User {
   name: String!,
}
```

`User` is an Object type in the example above.

<h2 id="operation">Operation</h2>
<p>A single query, mutation, or subscription that can be interpreted by a GraphQL execution engine.</p>

<h2 id="operation-name">Operation name</h2>
<p>A name for a single query, mutation, or subscription. Identifying a query or mutation by name is very useful for logging and debugging when something goes wrong in a GraphQL server.</p>

```js
mutation AddTodo($type: String!) {
  addTodo(type: $type) {
    id
    type
  }
}

query getHuman {
  human(id: "200") {
    weight(unit: "pounds")
    height
  }
}
```

`AddTodo` and `getHuman` are names for the mutation and query operation respectively.

<h2 id="partial-query-caching">Partial query caching</h2>
<p>A technique for caching inputs to GraphQL queries. This type of caching ensures that if the query is slightly different but with the same inputs, those inputs can simply be retrieved from the cache instead of fetching data again from the backend. It is implemented in Apollo Server 2 as Data Source caching.</p>

<h2 id="query">Query</h2>
<p>A read-only fetch operation to request data from a GraphQL service.</p>

<h2 id="query-colocation">Query colocation</h2>
<p>A practice of placing a GraphQL query in the same location as the app component's view logic.</p>

```js
const GET_DOG_PHOTO = gql`
 query dog($breed: String!) {
  dog(breed: $breed) {
    id
    displayImage
  }
}`;

export const queryComponent = `const DogPhoto = ({ breed }) => (
  <Query query={GET_DOG_PHOTO} variables={{ breed }}>
    {({ loading, error, data }) => {
      if (loading) return null;
      if (error) return 'Error!';
      return (
        <img src={data.dog.displayImage} />
      );
    }}
  </Query>
);`;
```

<h2 id="query-whitelisting">Query whitelisting</h2>
<p>A technique for preventing unwanted attacks by maintaining a list of approved queries that are allowed in your application. Any query not present in the list that is run against the server will not be allowed. [Automatic Persisted Queries](../guides/performance.html#automatic-persisted-queries) is a feature of Apollo Server 2 that enables query whitelisting and persisted queries.</p>

<h2 id="resolver">Resolver</h2>
<p>A function that connects schema fields and types to various backends. It can retrieve or write data from either an SQL, a No-SQL, graph database, a micro-service or a REST API.</p>


<h2 id="schema">Schema</h2>
<p>A GraphQL [schema](https://www.apollographql.com/docs/apollo-server/essentials/schema.html) is at the center of any GraphQL server implementation and describes the functionality available to the clients which connect to it.</p>


<h2 id="schema-definition-language">Schema Definition Language (SDL)</h2>
<p>The syntax for writing GraphQL Schemas. It is otherwise known as Interface Definition Language. It is the lingua franca shared by all for building GraphQL APIs regardless of the programming language chosen.</p>

```js
type Author {
  id: Int!
  firstName: String
  lastName: String
  posts: [Post]
}
type Post {
  id: Int!
  title: String
  author: Author
  votes: Int
}
type Query {
  posts: [Post]
  author(id: Int!): Author
}
```

<h2 id="schema-first-development">Schema first development</h2>
<p>A [development approach](https://www.apollographql.com/docs/fundamentals/tips.html#schema) for designing and building modern UIs that involves the frontend and backend teams agreeing on a Schema first, which serves as a contract between the UI and the backend before any API engineering happens.</p>


<h2 id="schema-registry">Schema registry</h2>
<p>A central database that enables schema registration, tracking of detailed schema changes e.g. types added, fields added, fields deprecated and looking up previous versions of schema.</p>


<h2 id="schema-versioning">Schema versioning</h2>
<p>Refers to the ability to have different versions of your Schema. This allows for reversible changes to be made to the Schema. The Apollo CLI is a tool that provides and manages Schema versioning with Engine.</p>


<h2 id="schema-stitching">Schema stitching</h2>
<p>The process of merging [different schemas into one GraphQL schema](./docs/graphql-tools/schema-stitching.html). These schemas can be local, remote or from third party services. In a microservice-style deployment model, where your data exists across multiple APIs, Schema stitching makes it possible to combine all of them into one schema that can be queried for all the data at once.</p>


<h2 id="subscription">Subscription</h2>
<p>A real-time GraphQL operation. A Subscription is defined in a schema like queries and mutations.</p>

```js
type Subscription {
  commentAdded(repoFullName: String!): Comment
}
...
subscription onCommentAdded($repoFullName: String!){
  commentAdded(repoFullName: $repoFullName){
    id
    content
  }
}
```

<h2 id="scalar-type">Scalar Type</h2>
<p>A type that qualifies the data a GraphQL field resolves. GraphQL ships with some scalar types out of the box; **Int**, **Float**, **String**, **Boolean** and **ID**. However, a [custom scalar](https://www.apollographql.com/docs/graphql-tools/scalars.html#custom-scalars) type such as **Date** can be specified in a GraphQL service implementation.</p>


<h2 id="type-system">Type System</h2>
<p>A collection of types which characterizes the set of data that can be validated, queried and executed on a GraphQL API.</p>


<h2 id="whole-response-caching">Whole response caching</h2>
<p>A technique used to cache entire results of GraphQL queries. This process improves performance by preventing the fetching of the same results from the server if it has been obtained before. Check out the [Apollo performance guide](../guides/performance.html).</p>