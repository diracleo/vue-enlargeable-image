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
      <h2>Photo Portfolio</h2>
      <div class="portfolio">
        <div>
          <enlargeable-image src="https://dane-iracleous-portfolio.s3-us-west-2.amazonaws.com/stock/demo1_small.jpg" src_large="https://dane-iracleous-portfolio.s3-us-west-2.amazonaws.com/stock/demo1_large.jpg" animation_duration="0" />
        </div>
        <div>
          <enlargeable-image src="https://dane-iracleous-portfolio.s3-us-west-2.amazonaws.com/stock/demo2_small.jpg" src_large="https://dane-iracleous-portfolio.s3-us-west-2.amazonaws.com/stock/demo2_large.jpg" animation_duration="2000" />
        </div>
        <div>
          <enlargeable-image src="https://dane-iracleous-portfolio.s3-us-west-2.amazonaws.com/stock/demo3_small.jpg" src_large="https://dane-iracleous-portfolio.s3-us-west-2.amazonaws.com/stock/demo3_large.jpg" />
        </div>
        <div>
          <enlargeable-image src="https://dane-iracleous-portfolio.s3-us-west-2.amazonaws.com/stock/demo4_small.jpg" src_large="https://dane-iracleous-portfolio.s3-us-west-2.amazonaws.com/stock/demo4_large.jpg" />
        </div>
        <div>
          <enlargeable-image src="https://dane-iracleous-portfolio.s3-us-west-2.amazonaws.com/stock/demo5_small.jpg" src_large="https://dane-iracleous-portfolio.s3-us-west-2.amazonaws.com/stock/demo5_large.jpg" />
        </div>
      </div>
      <h2>Text Links</h2>
      <div class="portfolio">
        <div>
          <enlargeable-image src="https://dane-iracleous-portfolio.s3-us-west-2.amazonaws.com/stock/demo1_small.jpg" src_large="https://dane-iracleous-portfolio.s3-us-west-2.amazonaws.com/stock/demo1_large.jpg">
            <span>Mouse</span>
          </enlargeable-image>
        </div>
        <div>
          <enlargeable-image src="https://dane-iracleous-portfolio.s3-us-west-2.amazonaws.com/stock/demo2_small.jpg" src_large="https://dane-iracleous-portfolio.s3-us-west-2.amazonaws.com/stock/demo2_large.jpg">
            <span>View</span>
          </enlargeable-image>
        </div>
        <div>
          <enlargeable-image src="https://dane-iracleous-portfolio.s3-us-west-2.amazonaws.com/stock/demo3_small.jpg" src_large="https://dane-iracleous-portfolio.s3-us-west-2.amazonaws.com/stock/demo3_large.jpg">
            <span>Upside-Down</span>
          </enlargeable-image>
        </div>
        <div>
          <enlargeable-image src="https://dane-iracleous-portfolio.s3-us-west-2.amazonaws.com/stock/demo4_small.jpg" src_large="https://dane-iracleous-portfolio.s3-us-west-2.amazonaws.com/stock/demo4_large.jpg">
            <span>Pathway</span>
          </enlargeable-image>
        </div>
        <div>
          <enlargeable-image src="https://dane-iracleous-portfolio.s3-us-west-2.amazonaws.com/stock/demo5_small.jpg" src_large="https://dane-iracleous-portfolio.s3-us-west-2.amazonaws.com/stock/demo5_large.jpg">
            <span>Rackets</span>
          </enlargeable-image>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.test-container {
  font-family:Arial;
}
.test-container h2 {
  text-align:center;
}
.test-container .portfolio {
  display:flex;
  justify-content:center;
  align-items:center;
  flex-wrap:wrap;
}
.test-container .portfolio > div {
  max-width:200px;
  margin:30px;
}
.test-container .portfolio > div .enlargeable-image-slot > img {
  max-width:100%;
}
</style>