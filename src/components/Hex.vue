<template lang="html">
  <div class="hexagon">
    <v-icon large style="position: absolute; left: 16px; top: 2px;" :color="color">{{ icon }}</v-icon>
  </div>
</template>

<script>
export default {
  props: ['icon', 'color']
}
</script>

<style lang="css" scoped>
.hexagon {
  position: relative;
  width: 70px;
  height: 40.41px;
  background-color: #222;
  margin: 20.21px 0;
  z-index: 1;
  cursor: pointer;
  transition-duration: 0.5s;
  transition-timing-function: ease;
}

.hexagon:before,
.hexagon:after {
  cursor: pointer;
  transition-duration: 0.5s;
  transition-timing-function: ease;
  content: "";
  position: absolute;
  width: 0;
  border-left: 35px solid transparent;
  border-right: 35px solid transparent;
}

.hexagon:before {
  bottom: 100%;
  border-bottom: 20.21px solid #222;
}

.hexagon:after {
  top: 100%;
  width: 0;
  z-index: 0;
  border-top: 20.21px solid #222;
}
.hexagon:hover {
  background: #333;
}
.hexagon:active {
  transform:scale(1.1);
}
.hexagon:hover:before{
  border-bottom:  20.21px solid #333;
}
.hexagon:hover:after {
  border-top:  20.21px solid #333;
}
</style>
