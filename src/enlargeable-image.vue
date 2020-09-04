<script>
export default {
  name: 'EnlargeableImage',
  props: {
    src: {
      type: String
    },
    src_large: {
      type: String
    },
  },
  data() {
    return {
      enlarging: this.enlarging,
      enlarged: this.enlarged,
      styles: this.styles
    };
  },
  methods: {
    init() {
      var self = this;
      self.updating = false;
      self.enlarging = false;
      self.enlarged = false;
      self.styles = {};
    },
    enlarge(event) {
      var self = this;
      if(!self.updating) {
        self.updating = true;
        var img = self.$refs.img;
        var rect = img.getBoundingClientRect();
        self.styles = {
          position: "absolute",
          left: Math.round(rect.left)+"px",
          top: Math.round(rect.top)+"px",
          width: Math.floor(rect.right - rect.left)+"px",
          height: Math.floor(rect.bottom - rect.top)+"px",
          backgroundImage: "url("+self.$props.src+")",
        };
        self.enlarging = true;
        setTimeout(function() {
          self.styles = {
            backgroundImage: "url("+self.$props.src+")",
          };
          setTimeout(function() {
            self.enlarged = true;
            self.updating = false;
          }, 1400);
        }, 0);
      }
    },
    reset(event) {
      var self = this;
      if(!self.updating) {
        self.updating = true;
        var img = self.$refs.img;
        var rect = img.getBoundingClientRect();
        self.enlarging = true;
        setTimeout(function() {
          self.enlarged = false;
          self.styles = {
            backgroundImage: "url("+self.$props.src+")",
            position: "fixed",
            left: Math.round(rect.left)+"px",
            top: Math.round(rect.top)+"px",
            width: Math.floor(rect.right - rect.left)+"px",
            height: Math.floor(rect.bottom - rect.top)+"px",
          };
          setTimeout(function() {
            self.enlarged = false;
            self.enlarging = false;
            self.updating = false;
          }, 1400);
        }, 0);
      }
    }
  },
  mounted: function() {
    var self = this;
    self.init();
  }
};
</script>

<template>
  <div class="enlargeable-image">
    <img :src="this.$props.src" @click="enlarge($event)" ref="img" v-bind:class="{ active: enlarging }" />
    <div v-if="enlarging" @click="reset($event)" class="enlargeable-image-full" v-bind:style="styles" v-bind:class="{ enlarging: enlarging, enlarged: enlarged }">
      <img v-if="!enlarged" :src="this.$props.src" />
      <img v-if="enlarged" :src="this.$props.src_large" />
    </div>
  </div>
</template>

<style scoped>
.enlargeable-image > img {
  max-width:100%;
  max-height:100%;
  cursor:zoom-in;
}
.enlargeable-image > img.active {
  opacity:0.3;
  filter:grayscale(100%);
}
.enlargeable-image .enlargeable-image-full {
  cursor:zoom-out;
  background-color:transparent;
  display:flex;
  align-items:center;
  justify-content:center;
  background-position: center center;
  background-repeat:no-repeat;
  background-size:contain;
  transition: all 1.4s;
}
.enlargeable-image .enlargeable-image-full > img {
  object-fit:contain;
  width:100%;
  height:100%;
}
.enlargeable-image .enlargeable-image-full.enlarging {
  position:fixed;
  left:0px;
  top:0px;
  width:100%;
  height:100%;
  background-color:transparent;
}
</style>
