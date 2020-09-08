<!--
  Author: Dane Iracleous <daneiracleous@gmail.com>
  Repository: https://github.com/diracleo/vue-enlargeable-image
-->
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
    trigger: {
      type: String,
      default: "click"
    }
  },
  data() {
    return {
      state: this.state,
      styles: this.styles
    };
  },
  methods: {
    init() {
      var self = this;
      self.state = "delarged";
      self.delay = 50;
      self.adjust_top = 0;
      self.wait = false;
      var transition_seconds = parseInt(self.$props.animation_duration) / 1000;
      if(transition_seconds == 0) {
        self.delay = 0;
      }
      transition_seconds = transition_seconds.toFixed(2);
      self.transition_value = "width "+transition_seconds+"s, height "+transition_seconds+"s, top "+transition_seconds+"s, left "+transition_seconds+"s, background-color "+transition_seconds+"s";
      self.styles = {
        transition: self.transition_value
      };
      if(self.$props.trigger == "hover") {
        self.styles.pointerEvents = "none";
      }
    },
    enlarge() {
      var self = this;
      var rect = self.$refs.slot.getBoundingClientRect();
      self.styles = {
        position: "fixed",
        left: Math.round(rect.left)+"px",
        top: Math.round(rect.top + self.adjust_top)+"px",
        width: Math.round(rect.right - rect.left)+"px",
        height: Math.round(rect.bottom - rect.top)+"px",
        backgroundImage: "url("+self.$props.src+")",
        transition: self.transition_value
      };
      if(self.$props.trigger == "hover") {
        self.styles.pointerEvents = "none";
      }
      self.state = "enlarging";
      if(typeof(self.timer) != 'undefined') {
        clearTimeout(self.timer);
      }
      self.timer = setTimeout(function() {
        self.$emit('enlarging');
        self.styles = {
          backgroundImage: "url("+self.$props.src+")",
          transition: self.transition_value
        };
        if(self.$props.trigger == "hover") {
          self.styles.pointerEvents = "none";
        }
        if(typeof(self.timer) != 'undefined') {
          clearTimeout(self.timer);
        }
        self.timer = setTimeout(function() {
          self.state = "enlarged";
          self.$emit('enlarged');
        }, self.$props.animation_duration);
      }, self.delay);
    },
    reset() {
      var self = this;
      if(self.state != "delarging") {
        var rect = self.$refs.slot.getBoundingClientRect();
        if(typeof(self.timer) != 'undefined') {
          clearTimeout(self.timer);
        }
        self.timer = setTimeout(function() {
          self.state = "delarging";
          self.$emit('delarging');
          self.styles = {
            backgroundImage: "url("+self.$props.src+")",
            position: "fixed",
            left: Math.round(rect.left)+"px",
            top: Math.round(rect.top + self.adjust_top)+"px",
            width: Math.round(rect.right - rect.left)+"px",
            height: Math.round(rect.bottom - rect.top)+"px",
            transition: self.transition_value
          };
          if(self.$props.trigger == "hover") {
            self.styles.pointerEvents = "none";
          }
          if(typeof(self.timer) != 'undefined') {
            clearTimeout(self.timer);
          }
          self.timer = setTimeout(function() {
            self.state = "delarged";
            self.$emit('delarged');
          }, self.$props.animation_duration);
        }, 0);
      } else {
        self.enlarge();
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
  <div v-bind:class="{ 'enlargeable-image': true, active: state != 'delarged' }">
    <div class="slot" ref="slot" v-on="this.$props.trigger == 'click' ? { click: enlarge } : { mouseenter: enlarge, mouseleave: reset }">
      <slot>
        <img :src="this.$props.src" class="default" />
      </slot>
    </div>
    <div class="full" v-bind:style="styles" v-bind:class="state" v-on="this.$props.trigger == 'click' ? { click: reset } : {}">
      <img v-if="state != 'enlarged'" :src="this.$props.src" />
      <img v-if="state == 'enlarged'" :src="this.$props.src_large" />
    </div>
  </div>
</template>

<style scoped>
/* your passed-in element */
.enlargeable-image > .slot {
  display:inline-block;
  max-width:100%;
  max-height:100%;
  cursor:zoom-in;
}
/* default img if no element passed in */
.enlargeable-image > .slot > img.default {
  max-width:100%;
  vertical-align:middle;
}
/* passed-in element when growth is happening */
.enlargeable-image.active > .slot {
  opacity:0.3;
  filter:grayscale(100%);
}
/* full version that grows (background image allows seamless transition from thumbnail to full) */
.enlargeable-image .full {
  cursor:zoom-out;
  background-color:transparent;
  align-items:center;
  justify-content:center;
  background-position: center center;
  background-repeat:no-repeat;
  background-size:contain;
  display:none;
}
.enlargeable-image .full > img {
  object-fit:contain;
  width:100%;
  height:100%;
}
/* full version while getting bigger */
.enlargeable-image .full.enlarging {
  display:flex;
  position:fixed;
  left:0px;
  top:0px;
  width:100%;
  height:100%;
  background-color:transparent;
  cursor:zoom-out;
  z-index:3;
}
/* full version while at its peak size */
.enlargeable-image .full.enlarged {
  display:flex;
  position:fixed;
  left:0px;
  top:0px;
  width:100%;
  height:100%;
  background-color:transparent;
  cursor:zoom-out;
  z-index:2;
}
/* full version while getting smaller */
.enlargeable-image .full.delarging {
  display:flex;
  position:fixed;
  left:0px;
  top:0px;
  width:100%;
  height:100%;
  background-color:transparent;
  cursor:zoom-in;
  z-index:1;
}
</style>