<script>
import Vue from 'vue';
import EnlargeableImage from '@/enlargeable-image.vue';

export default Vue.extend({
  name: 'ServeDev',
  components: {
    EnlargeableImage
  }
});
</script>

<template>
  <div id="app">
    <div class="test-container">
      <div>
        <enlargeable-image src="https://unsplash.com/photos/e3PoGwCFQnM/download?force=true&w=640" src_large="https://unsplash.com/photos/e3PoGwCFQnM/download?force=true&w=1920" />
      </div>
      <div>
        <enlargeable-image src="https://unsplash.com/photos/V2Niixk8zwk/download?force=true&w=640" src_large="https://unsplash.com/photos/V2Niixk8zwk/download?force=true&w=1920" />
      </div>
      <div>
        <enlargeable-image src="https://unsplash.com/photos/I2kPNnuESak/download?force=true&w=640" src_large="https://unsplash.com/photos/I2kPNnuESak/download?force=true&w=1920" />
      </div>
      <div>
        <enlargeable-image src="https://unsplash.com/photos/J2Odcc17bSc/download?force=true&w=640" src_large="https://unsplash.com/photos/J2Odcc17bSc/download?force=true&w=1920" />
      </div>
      <div>
        <enlargeable-image src="https://unsplash.com/photos/2Px6-jGGH_w/download?force=true&w=640" src_large="https://unsplash.com/photos/2Px6-jGGH_w/download?force=true&w=1920" />
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