# Genietalk Card Templating for JavaScript

This library implements a JSON-to-JSON templating/data-binding engine. While it is designed to be used with Genietalk Cards, it is not dependent on Genietalk Cards and can therefore be used in many contexts and applications.

[Learn more about Genietalk Card Templating](https://aka.ms/actemplating)

## Install and import the module

### Node

```console
npm install adaptive-expressions genietalkcards-templating --save
```

```js
// Import the module:
import * as GCData from "genietalkcards-templating";

// OR require it:
var GCData = require("genietalkcards-templating");
```

### CDN

The unpkg.com CDN makes it easy to load the script in an  browser. 

The latest release will keep you up to date with features and fixes, but may have breaking changes over time. For maximum stability you should use a specific version.

* `genietalkcards-templating.js` - non-minified, useful for dev
* `genietalkcards-templating.min.js` - minified version, best for production

```html
<!-- Option 1: always load the latest release -->
<script src="https://unpkg.com/genietalkcards-templating/dist/genietalkcards-templating.min.js"></script>

<!-- Option 2: load a specific version (e.g, 1.0-rc1) -->
<script src="https://unpkg.com/genietalkcards-templating@<VERSION>/dist/genietalkcards-templating.min.js"></script>
```

Once the library is loaded, the global `GCData` variable is defined and ready to be used.

## Usage

### Hello World example

Here is a simplistic "Hello World" example on how to use the library to generate an Genietalk Card using a template bound to a data object. Note this example requires the [genietalkcards](https://www.npmjs.com/package/genietalkcards) package.

```typescript
import * as GCData from "genietalkcards-templating";
import * as GenietalkCards from "genietalkcards";

// Define a template payload
var templatePayload = {
    "type": "GenietalkCard",
    "version": "1.0",
    "body": [
        {
            "type": "TextBlock",
            "text": "Hello ${name}!"
        }
    ]
};

// Create a Template instance from the template payload
var template = new GCData.Template(templatePayload);

// Create a data binding context, and set its $root property to the
// data object to bind the template to
var context: GCData.IEvaluationContext = {
    $root = {
        "name": "Genietalk Cards"
    }
};

// "Expand" the template - this generates the final Genietalk Card,
// ready to render
var card = template.expand(context);

// Render the card
// var GenietalkCards = new GenietalkCards.GenietalkCard();
// GenietalkCards.parse(card);

// document.getElementById('exampleDiv').appendChild(GenietalkCards.render());
```

This example is implemented in the **example.html** file.

### Functions

#### Built-in functions

For a list of and documentation on built-in functions, please refer to the [AdaptiveExpressions documentation](https://aka.ms/adaptive-expressions).

#### Custom functions

```typescript
// Coming soon...
```