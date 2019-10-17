## REST is **great** but let's have a look on some **shortcomings** 

!SUB
<!-- .slide: data-background="images/system.jpg" data-transition="slide" data-background-transition="fade" -->

<h1 style="color:yellow;font-size:100px;font-weight:600;">Assignment</h1>  

<p style="color:white;font-size:80px;font-weight:600;">Build an app that shows information of conferences, talks and speakers.</p>  



!SUB
<img data-src="images/model_0.png" height="80%" width="80%">

!SUB
<img data-src="images/model_1.png" height="80%" width="80%">

!SUB
<img data-src="images/model_2.png" height="80%" width="80%">


!SUB
## Under fetching
Resource: `/talks`
```json
[
  {
    "title" : "GraphQL - The Next API Language",
    "speaker" : {
      "id" : "niek",
      "href" : "http://someconference/speakers/niek"
    }
  }
  {
    "title" : "Built To Last ...and the end of migrations",
    "speaker" : {
      "id" : "adam",
      "href" : "http://someconference/speakers/adam"
    }
  }
]
```

!SUB
## Over fetching
Resource `/speakers/niek`

```json
{
  "id" : "niek",
  "name" : "Niek Palm",
  "twitter" : "niekos77",
  "blog" : "https://040code.github.io",
  "github": "npalm",
  "city" : "Eindhoven",
  "shoppinglist" : {
    "href" : "http://someconference/speakers/niek/shoppinglist"
  }
}
```

!SUB
## Many endpoints

![endpoints](images/endpoints.png)

!SUB

<!-- .slide: data-background="images/types.jpg" data-transition="none" data-background-transition="none" -->

<h1 style="color:yellow;font-size:100px;font-weight:600;">Non Typed</h1>  
