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
    animation_duration: {
      type: String,
      default: "700"
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
      var transition_seconds = parseInt(self.$props.animation_duration) / 1000;
      transition_seconds = transition_seconds.toFixed(2);
      self.transition_value = "width "+transition_seconds+"s, height "+transition_seconds+"s, top "+transition_seconds+"s, left "+transition_seconds+"s, background-color "+transition_seconds+"s";
      self.styles = {
        transition: self.transition_value
      };
    },
    enlarge() {
      var self = this;
      if(!self.updating) {
        self.updating = true;
        var img = self.$refs.img;
        var rect = img.getBoundingClientRect();
        self.styles = {
          position: "fixed",
          left: Math.ceil(rect.left)+"px",
          top: Math.floor(rect.top)+"px",
          width: Math.floor(rect.right - rect.left)+"px",
          height: Math.floor(rect.bottom - rect.top)+"px",
          backgroundImage: "url("+self.$props.src+")",
          transition: self.transition_value
        };
        self.enlarging = true;
        setTimeout(function() {
          self.$emit('enlarging');
          self.styles = {
            backgroundImage: "url("+self.$props.src+")",
            transition: self.transition_value
          };
          setTimeout(function() {
            self.enlarged = true;
            self.updating = false;
            self.$emit('enlarged');
          }, self.$props.animation_duration);
        }, 100);
      }
    },
    reset() {
      var self = this;
      if(!self.updating) {
        self.updating = true;
        var img = self.$refs.img;
        var rect = img.getBoundingClientRect();
        self.enlarging = true;
        setTimeout(function() {
          self.$emit('delarging');
          self.enlarged = false;
          self.styles = {
            backgroundImage: "url("+self.$props.src+")",
            position: "fixed",
            left: Math.ceil(rect.left)+"px",
            top: Math.floor(rect.top)+"px",
            width: Math.floor(rect.right - rect.left)+"px",
            height: Math.floor(rect.bottom - rect.top)+"px",
            transition: self.transition_value
          };
          setTimeout(function() {
            self.enlarged = false;
            self.enlarging = false;
            self.updating = false;
            self.$emit('delarged');
          }, self.$props.animation_duration);
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
    <div v-bind:class="{ 'enlargeable-image-slot': true, active: enlarging }" ref="img" @click="enlarge">
      <slot>
        <img :src="this.$props.src" />
      </slot>
    </div>
    <div @click="reset" class="enlargeable-image-full" v-bind:style="styles" v-bind:class="{ enlarging: enlarging, enlarged: enlarged }">
      <img v-if="!enlarged" :src="this.$props.src" />
      <img v-if="enlarged" :src="this.$props.src_large" />
    </div>
  </div>
</template>

<style scoped>
.enlargeable-image .enlargeable-image-slot {
  display:inline-block;
}
.enlargeable-image .enlargeable-image-slot > img {
  max-width:100%;
}
.enlargeable-image > .enlargeable-image-slot {
  max-width:100%;
  max-height:100%;
  cursor:zoom-in;
}
.enlargeable-image > .enlargeable-image-slot.active {
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
</style>
