# rss-parser

## Installation
```bash
npm install --save dlm-rss-parser
```

## Usage
rss-parser exposes `parseURL()`, `parseString()`, and `parseFile()` functions.

Check out the output format in [test/output/reddit.json](test/output/reddit.json)

### NodeJS
```js
var parser = require('dlm-rss-parser');

parser.parseURL('https://www.reddit.com/.rss', function(err, parsed) {
  console.log(parsed.feed.title);
  parsed.feed.entries.forEach(function(entry) {
    console.log(entry.title + ':' + entry.link);
  })
})
```

### Web
```html
<script src="node_modules/dlm-rss-parser/dist/dlm-rss-parser.js"></script>
<script>
RSSParser.parseURL('https://www.reddit.com/.rss', function(err, parsed) {
  console.log(parsed.feed.title);
  parsed.feed.entries.forEach(function(entry) {
    console.log(entry.title + ':' + entry.link);
  })
})
</script>
```

## Contributing

### Running Tests
The tests run the RSS parser for several sample RSS feeds in `test/input` and outputs the resulting JSON into `test/output`. If there are any changes to the output files the tests will fail.

To check if your changes affect the output of any test cases, run

`npm test`

To update the output files with your changes, run

`WRITE_GOLDEN=true npm test`

### Publishing Releases
```bash
grunt browserify
git commit -a -m "browserify"
npm version minor # or major/patch
npm publish
git push --follow-tags
```

