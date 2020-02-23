<template lang="html">
  <div class="hexagon" :class="color" :style="{ backgroundImage: image ? 'linear-gradient(rgba(0, 0, 0, 0.6), rgba(0, 0, 0, 0.6)),url(' + image + ')'  : ''}">
    <div class="hexTop"></div>
    <h1>{{ text }}</h1>
    <div class="hexBottom"></div>
  </div>
</template>

<script>
export default {
  props: ['text', 'image', 'color']
}
</script>

<style lang="css" scoped>
.hexagon {
  cursor: pointer;
  position: relative;
  width: 300px;
  height: 173.21px;
  margin: 86.60px 0;
  background-size: auto 346.4102px;
  background-position: center;
  transition-duration: 0.5s;
  transition-timing-function: ease;
}
.hexagon:hover{
  transform: rotate(10deg) scale(0.9);
}
.hexTop,
.hexBottom {
  position: absolute;
  width: 212.13px;
  height: 212.13px;
  overflow: hidden;
  -webkit-transform: scaleY(0.5774) rotate(-45deg);
  -ms-transform: scaleY(0.5774) rotate(-45deg);
  transform: scaleY(0.5774) rotate(-45deg);
  background: inherit;
  left: 43.93px;
}

/*counter transform the bg image on the caps*/
.hexTop:after,
.hexBottom:after {
  content: "";
  position: absolute;
  width: 300.0000px;
  height: 173.20508075688775px;
  -webkit-transform:  rotate(45deg) scaleY(1.7321) translateY(-86.6025px);
  -ms-transform:      rotate(45deg) scaleY(1.7321) translateY(-86.6025px);
  transform:          rotate(45deg) scaleY(1.7321) translateY(-86.6025px);
  -webkit-transform-origin: 0 0;
  -ms-transform-origin: 0 0;
  transform-origin: 0 0;
  background: inherit;
}

.hexTop {
  top: -106.0660px;
}

.hexTop:after {
  background-position: center top;
}

.hexBottom {
  bottom: -106.0660px;
}

.hexBottom:after {
  background-position: center bottom;
}

.hexagon:after {
  content: "";
  position: absolute;
  top: 0.0000px;
  left: 0;
  width: 300.0000px;
  height: 173.2051px;
  background: inherit;
}
h1{
  width: 100%; z-index: 1;
  font-size: 4em;
  text-align: center;
  position: absolute;
  transform: translate(-50%, -50%); top: 50%; left: 50%;
  transition-duration: 0.5s;
  transition-timing-function: ease;
}
</style>
