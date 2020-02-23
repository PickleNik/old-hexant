<template lang="html">
  <div class="hexagon" :class="color" :style="{ backgroundImage: image ? 'linear-gradient(rgba(0, 0, 0, 0.6), rgba(0, 0, 0, 0.6)),url(' + image + ')'  : ''}">
    <div class="hexTop"></div>
    <h2>{{ text }}</h2>
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
  width: 200px;
  height: 115.47px;
  margin: 57.74px 0;
  background-image: url(http://csshexagon.com/img/meow.jpg);
  background-size: auto 230.9401px;
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
  width: 141.42px;
  height: 141.42px;
  overflow: hidden;
  -webkit-transform: scaleY(0.5774) rotate(-45deg);
  -ms-transform: scaleY(0.5774) rotate(-45deg);
  transform: scaleY(0.5774) rotate(-45deg);
  background: inherit;
  left: 29.29px;
}

/*counter transform the bg image on the caps*/
.hexTop:after,
.hexBottom:after {
  content: "";
  position: absolute;
  width: 200.0000px;
  height: 115.47005383792516px;
  -webkit-transform:  rotate(45deg) scaleY(1.7321) translateY(-57.7350px);
  -ms-transform:      rotate(45deg) scaleY(1.7321) translateY(-57.7350px);
  transform:          rotate(45deg) scaleY(1.7321) translateY(-57.7350px);
  -webkit-transform-origin: 0 0;
  -ms-transform-origin: 0 0;
  transform-origin: 0 0;
  background: inherit;
}

.hexTop {
  top: -70.7107px;
}

.hexTop:after {
  background-position: center top;
}

.hexBottom {
  bottom: -70.7107px;
}

.hexBottom:after {
  background-position: center bottom;
}

.hexagon:after {
  content: "";
  position: absolute;
  top: 0.0000px;
  left: 0;
  width: 200.0000px;
  height: 115.4701px;
  background: inherit;
}
h2{
  width: 100%; z-index: 1;
  font-size: 2em;
  text-align: center;
  position: absolute;
  transform: translate(-50%, -50%); top: 50%; left: 50%;
  transition-duration: 0.5s;
  transition-timing-function: ease;
}
</style>
