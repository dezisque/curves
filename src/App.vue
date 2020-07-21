<template>
  <div id="app">
    <svg>
      <circle :cx="x1" :cy="y1" r="8" fill="green" ref="circle1" @mousedown="changePointCoords"></circle>
      <line :x1="x1" :y1="y1" :x2="x2" :y2="y2" stroke="green" stroke-width="2"></line>
      <circle :cx="x2" :cy="y2" r="8" fill="green" ref="circle2" @mousedown="changePointCoords"></circle>
    </svg>
  </div>
</template>

<script>

export default {
  name: 'App',
  data(){
    return{
      x1: 5,
      x2: 55,
      y1: 5,
      y2: 55,
    }
  },
  methods: {
    changePointCoords(){
      window.addEventListener("mousemove", this.mousemoveHandler);
      window.addEventListener("mouseup", this.mouseupHandler);
    },
    mousemoveHandler(e){
      switch (e.srcElement) {
        case (this.$refs.circle1):
          this.x1 = e.offsetX;
          this.y1 = e.offsetY;
          break;
        case (this.$refs.circle2):
          this.x2 = e.offsetX;
          this.y2 = e.offsetY;
          break;
      }
    },
    mouseupHandler(){
      window.removeEventListener("mousemove", this.mousemoveHandler);
      window.removeEventListener("mouseup", this.mouseupHandler);
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
svg{
  border: 2px solid black;
}
</style>
