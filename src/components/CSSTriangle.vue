<template>
  <div id="one"> </div>
  <div id="two"> </div>
</template>

<script>
export default {
  name: 'CssTriangle'
}

</script>

<style scoped>
#one {
  border-style: solid;
  border-width: 100px 50px 0 50px;
  border-color: blue transparent transparent transparent;
  background: transparent;
  width:  0px;
  height: 0px;
  /*box-shadow: 0 0 1em black;*/
  filter: drop-shadow(0 0 1em cyan);
}

#two {
  background: red;
  width:  100px;
  height: 100px;
  clip-path: polygon(0 0, 100% 50%, 0 100%);
  box-shadow: inset 0 0 1em black;
}
</style>
