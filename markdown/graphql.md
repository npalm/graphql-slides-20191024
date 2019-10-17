
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
<img  data-src="images/giphy-hackerman.gif" height="100%" width="100%">

!SUB

<!-- .slide: data-background-iframe="http://localhost:4466" -->

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
### GraphQL Queries : Arguments

In REST you pass a single set of arguments as query parameters in GraphQL **every field and nested object** can get its own set.

<pre class="fragment"><code>
{                       {
  person(id: 1)           "data": {
    name                     "person" {
  }                             "name": "Niek Palm"
}                            }
                          }
                        }
</code></pre>

!SUB
### GraphQL Queries : Aliases
**Aliases** let you rename the result of a field to anything you want.
<pre class="fragment"><code>
{                                 {
  person(id: 1)                     "data": {
    name                              "person" {
  }                                       "name": "Niek Palm"
}                                      }
                                    }
                                  }

</code></pre>


!SUB
### GraphQL Queries : Aliases
**Aliases** let you rename the result of a field to anything you want.
<pre><code>
{                                 {
  speaker: person(id: 1)            "data": {
    fullName: name                    "speaker" {
  }                                       "fullName": "Niek Palm"
}                                      }
                                    }
                                  }

</code></pre>

!SUB
### GraphQL Queries : Fragments
GraphQL includes reusable units called **fragments**. Fragments let you construct sets of fields, and then include them in queries.

<pre class="fragment"><code>
fragment details on Person {
  name
  github
}
</code></pre>


!SUB
### GraphQL Queries : Variables
A GraphQL query can be parameterized with variables, maximizing query reuse, and avoiding costly string building in clients at runtime.

<div class="fragment" align="left">

```json
// HTTP POST request body
{  
  "query" : "query Query($id: Long!) {person($id: Long!) { name }}",
  "variables" : {"id":11}
}
```


!SUB
# DEMO
<img data-src="images/giphy-programming.gif" height="60%" width="60%">


!SUB
### GraphQL Mutations

Any operations that cause writes should be sent explicitly via a mutation. To call a mutation, you must use the keyword **mutation** before your GraphQL query


!SUB
### GraphQL Mutations

```
mutation {
  addPerson(person: {name: "Edsgar"}) {
    id
    name
  }
}

```

!SUB
# DEMO
<img data-src="images/giphy-bart.gif" height="60%" width="60%">


!SUB
### GraphQL Subscriptions

<div class="fragment" align="left">

```
subscription {
  comments {
    comment
    author
  }
}
```

<div class="fragment" align="left">

```json
"data" : {
  "comments" : {
    "comment" : "Testing shows the presence,
                 not the absence of bugs"
    "author" : "Edsgar"
  }
}
```

!SUB
# DEMO
<img data-src="images/giphy-programming2.gif" height="60%" width="60%">



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

// types for Talk and InputConference omitted.
```

!SUB
<!-- .slide: data-background-size="contain" data-background="images/graphql-java.jpg" data-transition="slide" data-background-transition="fade" -->

### Code first
<br><br><br><br><br><br><br><br><br><br><br><br><br>



!SLIDE
<!-- .slide: data-background-size="fit" data-background="images/architecture.jpg" data-transition="slide" data-background-transition="fade" -->

<p style="color:white;font-size:150px;font-weight:600;text-shadow: rgb(34, 34, 34) 5px 5px;">GraphQL Architecture</p>  


!SUB

<img data-src="images/single.png" height="100%" width="100%">

!SUB

<img data-src="images/combined.png" height="100%" width="100%">

!SUB

<img data-src="images/prisma-yoga.png" height="100%" width="100%">

!SUB
<!-- .slide: data-background-iframe="https://github.com/npalm/graphql-prisma-demo/blob/611223e6f2f410d4b284cf7128f63250a2145bdf/cities/datamodel.prisma" -->



!SUB
### Also Cool
- Backend As A Service [Graph Cool](https://www.graph.cool/) 
- GraphQL for datastores: [Postgres](https://github.com/graphile/postgraphile) / [Neo4j](https://github.com/neo4j-graphql)
- Write a static blog using React and GraphQL, [Gatsby](https://www.gatsbyjs.org/)
- gRPC with GraphQL [Google rejoiner](https://github.com/google/rejoiner)

