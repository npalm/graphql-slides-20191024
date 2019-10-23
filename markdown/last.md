![thanks](images/tux.png)


```
query {  
  me {
    name
    gtihub
    linkedin
    twitter
    blog
    talk {
        tittle
        slides
        repos
    }
  }
}

```

!SUB
![thanks](images/tux.png)

```json
{
  "data": {
    "name": "Niek Palm",
    "github": "npalm",
    "linkedin": "www.linkedin.com/in/niekpalm",
    "twitter": "niekos77",
    "blog": "https://040code.github.io",
    "talk": {
      "title": "GraphQL - The next API language",
      "slides": "npalm.github.io/graphql-slides-20191024/",
      "repos": "npalm.github.io/graphql"
    }
  }
}
```
