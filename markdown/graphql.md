
<!-- .slide: data-background="images/next.jpg" data-transition="none" data-background-transition="none" -->


<img data-src="images/graphql-logo.png" height="40%" width="40%">
<h1 style="color:hotpink;font-size:100px;font-weight:600;">GraphQL</h1>  

!SUB
# What is GraphQL

<ul>
<li class="fragment">GraphQL is a query language for APIs</li>
<li class="fragment">GraphQL provides a complete and understandable description of the data in your API</li>
<li class="fragment">The flexibility gives clients power and makes it easier to evolve APIs</li>
</ul>


!SUB
## What is GraphQL
<table class="reveal">
  <tr>
    <td class="fragment"><img data-src="images/graphql-describe.png"></td>
    <td class="fragment"><img data-src="images/graphql-ask.png"></td>
    <td class="fragment"><img data-src="images/graphql-get.png"></td>
  </tr>
</table>
  

!SUB
## Hello World

![hello-1](images/hello1.png)

!SUB
## Hello World
![hello-2](images/hello2.png)


!SUB
### Specification
![spec](images/spec.png)

!SUB
<img data-src="images/graphql-foundation.png" height="50%" width="50%">


"GraphQL has redefined how developers work with APIs and client-server interactions," said **Chris Aniszczyk**, Linux Foundation 

The Linux Foundation set up the GraphQL Foundation to work under an open governance model, with the intent of encouraging participation and technical contribution.



!SUB
### Supporting / using GraphQL

<img data-src="images/users.png" height="100%" width="100%">

(a selection)


!SUB
# DEMO
<img  data-src="images/giphy-hackerman.gif" height="70%" width="70%">


!SUB

<!-- .slide: data-background-iframe="http://localhost:8080/playground" -->

!SUB

<!-- .slide: data-background="images/inside.jpg" data-transition="none" data-background-transition="none" -->
<h1 style="color:white;font-size:150px;font-weight:600;text-shadow: rgb(34, 34, 34) 5px 5px;">Inside?</h1>  
    


!SUB
### Demo internals

<br>

![demo-1-1](images/demo-1-1.png)


!SUB
### Demo internals

<br>

![demo-1-3](images/demo-1-2.png)


!SUB
## Schema
A GraphQL schema is in essence the definition of a type system

<pre><code class="fragment">
schema {
    query: Query,
}

type Query {
  conference(id: ID!): Conference
  conferences: [Conference]
}

type Conference {
    id: ID!
    name: String!
    city: String
}

</code></pre>


!SUB
### HTTP request
<div class="fragment" align="left">

```json
// HTTP POST request body
{  
   "query":"query { conferences { name } }"
}
```

<div class="fragment" align="left">

```json
// HTTP response body
{  
   "data": {  
      "conferences": [  
         {  
            "name": "..."
         }
      ]
   }
}
```

!SLIDE
### GraphQL Queries

<br>

<table class="reveal">
  <tr class="fragment">
    <td>Arguments</td>
    <td>query parameters</td>
  </tr>
  <tr class="fragment">
    <td>Aliases</td>
    <td>rename the result of a field to anything </td>
  <tr class="fragment">
    <td>Fragments</td>
    <td>construct a set of fields and include</td>
  </tr>
  <tr class="fragment">
    <td>Variables</td>
    <td>parameterized for maximizing reuse</td>
  </tr>
</table>



!SUB
# DEMO
<img data-src="images/giphy-programming.gif" height="60%" width="60%">


!SUB

<!-- .slide: data-background-iframe="http://localhost:8080/playground" -->


!SUB
### GraphQL Mutations

Any operations that cause writes should be sent explicitly via a mutation. To call a mutation, you must use the keyword **mutation** before your GraphQL query


!SUB
### GraphQL Subscriptions

Subscriptions are a way to push data from the server to the clients that choose to listen to **real time messages** from the server. Subscriptions are **similar to queries** in that they specify a set of fields to be delivered.


!SUB
# DEMO
<img data-src="images/giphy-bart.gif" height="60%" width="60%">


!SUB

<!-- .slide: data-background-iframe="http://localhost:8080/playground" -->


!SLIDE
### How to start implementing
![lang](images/graphql-languages-lib.png)

[GraphQL.org](https://graphql.org) and [Awesome GraphQL](https://github.com/chentsulin/awesome-graphql)

!SUB
### Demo implementation
![](images/sample-java.png)


- java
- spring boot
- graphql java kickstart - spring boot starter
- graphql java kickstart - graphql java tools

<i class="fab fa-github fa-lg"></i> https://github.com/npalm/graphql-java-demo



!SUB

### Schema First

```
schema {
    query: Query,
}

type Query {
    conferences(filter: InputConference): [Conference!]
}

type Conference {
    id: ID!
    name: String!
    city: String,
    talks: [Talk!]
}
```

!SUB
### Define resolver function

```java
public class Conference extends BaseEntity {
    private String name;
    private String city;
    private List<Talk> talks;
}

public class Query implements GraphQLQueryResolver {

   public List<Conference> conferences(InputConference filter) {
        return service.find(filter);
    }
}

// types for BaseEntity, Talk and InputConference omitted.
```

!SUB
<!-- .slide: data-background-size="contain" data-background="images/graphql-java.jpg" data-transition="slide" data-background-transition="fade" -->

### Code first
<br><br><br><br><br><br><br><br><br><br><br><br><br>



!SLIDE
<!-- .slide: data-background-size="fit" data-background="images/architecture.jpg" data-transition="slide" data-background-transition="fade" -->

<p style="color:white;font-size:150px;font-weight:600;text-shadow: rgb(34, 34, 34) 5px 5px;">GraphQL Architecture</p>  


!SUB
### Connected data source(s)
<img data-src="images/single.png" height="100%" width="100%">

!SUB

### integrates existing systems
<img data-src="images/combined.png" height="100%" width="100%">


!SLIDE
<!-- .slide: data-background-size="fit" data-background="images/server.jpg" data-transition="slide" data-background-transition="fade" -->

<p style="color:lightblue;font-size:150px;font-weight:600;text-shadow: rgb(34, 34, 34) 5px 5px;">Serverless?</p>  


!SUB
### Serverless GraphQL
<br>

<table class="reveal">
  <tr class="fragment">
    <td>Prisma</td>
    <td>schema based on types and relations</td>
  </tr>
  <tr class="fragment">
    <td>AWS AppSync</td>
    <td>AWS serverless for GraphQL</td>
  </tr>
  <tr class="fragment">
    <td>Apollo</td>
    <td>Run apollo server as a function</td>
  </tr>
</table>



!SLIDE
<!-- .slide: data-background-size="fit" data-background="images/table.jpg" data-transition="slide" data-background-transition="fade" -->

<p style="color:lightyellow;font-size:130px;font-weight:600;text-shadow: rgb(34, 34, 34) 5px 5px;">Let's mix a bit!</p>  


!SUB
### Integrate domains

<img data-src="images/conferece-touristy.png" height="90%" width="90%">

!SUB
### Integrate domains

<img data-src="images/conferece-touristy-2.png" height="90%" width="90%">


!SUB
### Combine APIs

<img data-src="images/prisma-yoga.png" height="100%" width="100%">

<i class="fab fa-github fa-lg"></i> github.com/npalm/graphql-prisma-yoga-demo

!SUB
# DEMO
<img data-src="images/giphy-programming2.gif" height="60%" width="60%">


!SUB

<!-- .slide: data-background-iframe="http://localhost:4000" -->


!SUB
### Also cool
 
- [Gatsby](https://www.gatsbyjs.org/) - Static blog with React and GraphQL 
- [Apollo Engine](https://engine.apollographql.com) - GraphQL as a service 
- [Hasura](https://github.com/hasura/graphql-engine) - Instant GraphQL on Postgres
- [postgraphile](https://github.com/graphile/postgraphile) - GraphQL and PostgreSQL
- [graphql-voyager](https://github.com/APIs-guru/graphql-voyager) - Visually explore 
- [Google rejoiner](https://github.com/google/rejoiner) - gRPC with GraphQL
- [GrandSTACK and Neo4j](https://neo4j.com/labs/grandstack-graphql/)