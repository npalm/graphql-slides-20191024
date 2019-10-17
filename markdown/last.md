![thanks](images/tux.png)


```
query {  
  me {
    name
    twitter
    blog
    talk {
        tittle
        slides
        demo
    }
  }
}

```

!SUB
![thanks](images/tux.png)

```
{
  "data": {
    "name": "Niek Palm",
    "twitter": "niekos77",
    "blog": "https://040code.github.io",
    "talk": {
      "title": "GraphQL - The next generation API language",
      "slides": "https://npalm.github.io/graphql-slides-20180913/",
      "demo": "https://github.com/npalm/graphql-java-demo"
    }
  }
}
```
