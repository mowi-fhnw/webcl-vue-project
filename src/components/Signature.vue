<template>
  <div id="signature" v-on:click="this.isActive=true;this.signature();" v-bind:v-class="{anim: isActive}">
    <svg viewBox="0 -2 43 62" fill="none" xmlns="http://www.w3.org/2000/svg">
      <path ref="path0" d="M18 12V45" stroke="black"/>
      <path ref="path1" d="M35 4C35 4 19.5 24 19.5 28.5C19.5 33 38.5 56 38.5 56" stroke="black"/>
      <path ref="path2"
            d="M1.00002 14C2.24347 7.31013 30 13 9.00002 2C21.2046 -0.449153 26.0539 2.28554 33 8.5C45 19.236 44.5 43 33 52.5C21.5 62 14 55 6.99999 54"
            stroke="black"/>
    </svg>
  </div>
</template>

<script>
export default {
  name: 'Signature',
  data: function () {
    return {
      pathInfo: [],
      isActive: false
    }
  },
  methods: {
    linear: x => x,

    animate: function (tweening, millisecs, callback, onDone) {
      let start = null;

      function paint(timestamp) {
        if (!start) start = timestamp;
        const progress = timestamp - start;
        const fraction = progress / millisecs;
        const value = tweening(fraction);
        callback(value);
        if (progress < millisecs) {
          window.requestAnimationFrame(paint);
        } else {
          callback(1);
          if (onDone) onDone();
        }
      }

      callback(0);
      window.requestAnimationFrame(paint);
    },

    signature: function () {
      this.isActive = true;
      this.animate(this.linear, 500, this.animateStroke(0),
          () => this.animate(this.linear, 1500, this.animateStroke(2),
              () => this.animate(this.linear, 1000, this.animateStroke(1))
          ))
    },
    animateStroke: function (n) {
      return this.draw(n);
    },

    draw: function (n, fraction) {
      const total = this.pathInfo[n].total;
      this.pathInfo[n].style['stroke-dashoffset'] = total * (1 - fraction);
    }
  },
  mounted() {
    this.pathInfo = [
      this.$refs.path0,
      this.$refs.path1,
      this.$refs.path2,
    ]
    this.pathInfo.forEach(it => {
      it.total = it.getTotalLength();
      it.style['stroke-dasharray'] = it.total; // dash with full length, followed by equal empty space
      it.style['stroke-dashoffset'] = it.total; // show the empty space
    })
  }
}

</script>

<style scoped>
body {
  margin: 4rem;
  box-sizing: border-box;
  width: 100%;
  height: 100%;
  background-color: black;
}

main {
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
}

#signature {
  width: 60vw;
  height: 50vh;
}

svg {
  width: 100%; /* try to fill the container but keep aspect ratio */
  height: 100%;
  filter: drop-shadow(0px 0px 1em cyan);
}

svg path {
  stroke-width: 3px;
  stroke-opacity: 1;
  stroke-linecap: round;
  stroke: cyan;
}

.anim {
  transform: rotate(20deg) scaleX(2);
  transition: transform ease-out 2.5s;
  transition-delay: .5s;
}
</style>
