<script>
import Vue from 'vue';
import VueEnlargeableImage from '@/vue-enlargeable-image.vue';

export default Vue.extend({
  name: 'ServeDev',
  components: {
    VueEnlargeableImage
  }
});
</script>

<template>
  <div id="app">
    <div class="test-container">
      <div>
        <vue-enlargeable-image src="https://unsplash.com/photos/e3PoGwCFQnM/download?force=true&w=640" src_large="https://unsplash.com/photos/e3PoGwCFQnM/download?force=true&w=2400" />
      </div>
      <div>
        <vue-enlargeable-image src="https://unsplash.com/photos/e3PoGwCFQnM/download?force=true&w=640" src_large="https://unsplash.com/photos/e3PoGwCFQnM/download?force=true&w=2400" />
      </div>
      <div>
        <vue-enlargeable-image src="https://unsplash.com/photos/e3PoGwCFQnM/download?force=true&w=640" src_large="https://unsplash.com/photos/e3PoGwCFQnM/download?force=true&w=2400" />
      </div>
      <div>
        <vue-enlargeable-image src="https://unsplash.com/photos/e3PoGwCFQnM/download?force=true&w=640" src_large="https://unsplash.com/photos/e3PoGwCFQnM/download?force=true&w=2400" />
      </div>
      <div>
        <vue-enlargeable-image src="https://unsplash.com/photos/e3PoGwCFQnM/download?force=true&w=640" src_large="https://unsplash.com/photos/e3PoGwCFQnM/download?force=true&w=2400" />
      </div>
      <div>
        <vue-enlargeable-image src="https://unsplash.com/photos/e3PoGwCFQnM/download?force=true&w=640" src_large="https://unsplash.com/photos/e3PoGwCFQnM/download?force=true&w=2400" />
      </div>
      <div>
        <vue-enlargeable-image src="https://unsplash.com/photos/e3PoGwCFQnM/download?force=true&w=640" src_large="https://unsplash.com/photos/e3PoGwCFQnM/download?force=true&w=2400" />
      </div>
      <div>
        <vue-enlargeable-image src="https://unsplash.com/photos/e3PoGwCFQnM/download?force=true&w=640" src_large="https://unsplash.com/photos/e3PoGwCFQnM/download?force=true&w=2400" />
      </div>
      <div>
        <vue-enlargeable-image src="https://unsplash.com/photos/e3PoGwCFQnM/download?force=true&w=640" src_large="https://unsplash.com/photos/e3PoGwCFQnM/download?force=true&w=2400" />
      </div>
      <div>
        <vue-enlargeable-image src="https://unsplash.com/photos/e3PoGwCFQnM/download?force=true&w=640" src_large="https://unsplash.com/photos/e3PoGwCFQnM/download?force=true&w=2400" />
      </div>
      <div>
        <vue-enlargeable-image src="https://unsplash.com/photos/e3PoGwCFQnM/download?force=true&w=640" src_large="https://unsplash.com/photos/e3PoGwCFQnM/download?force=true&w=2400" />
      </div>
      <div>
        <vue-enlargeable-image src="https://unsplash.com/photos/e3PoGwCFQnM/download?force=true&w=640" src_large="https://unsplash.com/photos/e3PoGwCFQnM/download?force=true&w=2400" />
      </div>
      <div>
        <vue-enlargeable-image src="https://unsplash.com/photos/e3PoGwCFQnM/download?force=true&w=640" src_large="https://unsplash.com/photos/e3PoGwCFQnM/download?force=true&w=2400" />
      </div>
    </div>
  </div>
</template>

<style scoped>
.test-container {
  display:flex;
  justify-content:center;
  align-items:center;
  flex-wrap:wrap;
}
.test-container > div {
  width:200px;
  margin:30px;
}
</style>