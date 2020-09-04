# vue-enlargeable-image

A Vue component that acts as a wrapper around any other component to allow that component to be the clicked to show a fullscreen image using a smooth animation.

![](https://dane-iracleous-portfolio.s3-us-west-2.amazonaws.com/stock/vue-enlargeable-image.gif)


## Requirements

- [Vue.js](https://github.com/vuejs/vue)

## Installation

### npm

```bash

$ npm install @diracleo/vue-enlargeable-image

```

### external script

```html

<script src="https://unpkg.com/@diracleo/vue-enlargeable-image/dist/vue-enlargeable-image.min.js"></script>

```

## Usage

main.js:

```javascript

import Vue from 'vue'
import App from './App.vue'
import EnlargeableImage from '@diracleo/vue-enlargeable-image';

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

<!-- typical example using an img element -->
<enlargeable-image src="/path/to/thumbnail.jpg" src_large="/path/to/fullsize.jpg" animation_duration="700">
  <img src="/path/to/thumbnail.jpg" />
</enlargeable-image>

<!-- but you can use any component or HTML element you want -->
<enlargeable-image src="/path/to/thumbnail.jpg" src_large="/path/to/fullsize.jpg" animation_duration="700">
  <span>Click me to see the image</span>
</enlargeable-image>

```

## Properties

| Property           | Type        | Default           | Required | Description                              |
| ------------------ | ----------- | ----------------- | -------- | ---------------------------------------- |
| src                | String      | N/A               | *yes*    | Relative path or absolute URL to the thumbnail image                       |
| src_large          | String      | N/A               | *yes*    | Relative path or absolute URL to the full size image                       |
| animation_duration | String      | 700               | *no*     | How many milliseconds that the enlarging and delarging animation will take |


## Events

| Name          | Arguments                                | Description                               |
| ------------- | ---------------------------------------- | ----------------------------------------- |
| **enlarging** | None                                     | Fired when image starts to get bigger     |
| **enlarged**  | None                                     | Fired when image has been enlarged        |
| **delarging** | None                                     | Fired when image starts to get smaller    | 
| **delarged**  | None                                     | Fired when image is back to original size |


## Styling the component

```CSS

.enlargeable-image .enlargeable-image-slot {
  display:inline-block;
}
.enlargeable-image > div:first-child {
  max-width:100%;
  max-height:100%;
  cursor:zoom-in;
}
.enlargeable-image > div:first-child.active {
  opacity:0.3;
  filter:grayscale(100%);
}
.enlargeable-image .enlargeable-image-full {
  cursor:zoom-out;
  background-color:transparent;
  align-items:center;
  justify-content:center;
  background-position: center center;
  background-repeat:no-repeat;
  background-size:contain;
  z-index:2000;
  display:none;
}
.enlargeable-image .enlargeable-image-full > img {
  object-fit:contain;
  width:100%;
  height:100%;
}
.enlargeable-image .enlargeable-image-full.enlarging {
  display:flex;
  position:fixed;
  left:0px;
  top:0px;
  width:100%;
  height:100%;
  background-color:transparent;
}
.enlargeable-image .enlargeable-image-full.enlarged {
  display:flex;
}

```