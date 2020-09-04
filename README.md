# vue-enlargeable-image

Use in place of an img element to allow it to be enlarged to the full width and height of the browser window with a smooth animation.

## Requirements

- [Vue.js](https://github.com/vuejs/vue)

## Installation

### npm

```bash

$ npm install vue-enlargeable-image

```

## Usage

main.js:

```javascript

import Vue from 'vue'
import App from './App.vue'
import EnlargeableImage from 'vue-enlargeable-image';

Vue.use(EnlargeableImage)

new Vue({
  el: 'body',
  components: {
    App
  }
})

```

template:

```html
<enlargeable-image src="https://unsplash.com/photos/e3PoGwCFQnM/download?force=true&w=640" src_large="https://unsplash.com/photos/e3PoGwCFQnM/download?force=true&w=1920" />
```