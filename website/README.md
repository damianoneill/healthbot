This website was created with [Docusaurus](https://docusaurus.io/).

# Test environment

```sh
docker-compose up
```

This will run a [local web server](http://localhost:3000/healthbot/docs/intro).

# Publish

```sh
npm run build
```

Then

```sh
GIT_USER=damianoneill CURRENT_BRANCH=master USE_SSH=true npm run publish-gh-pages
```

# Full Documentation

Full documentation can be found on the [website](https://docusaurus.io/).
