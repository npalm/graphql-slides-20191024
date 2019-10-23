# GraphQL - The next API language
Slide deck for talk at [Codemotion Milan 2019](https://events.codemotion.com/conferences/milan/2019/), slides available via GitHub pages: https://npalm.github.io/graphql-slides-20191024

## Related
Other slide decks and repo's for demo's are grouped here: http://npalm.github.io/graphql

## slides
For the slides we use the [RevealJS](https://github.com/hakimel/reveal.js/) framework.
- See index.html for the slide show composition
- See markdown/* for the slide sources.

### Run the slides from sources
- You can also run the slides locally in a container from sources.
```
docker run -d -p 8080:80 --name slides \
  -v ${PWD}:/usr/share/nginx/html nginx
```
- Or use yarn
```
yarn && yarn start
```
- Open a browser [slides](http://localhost:9000/)
