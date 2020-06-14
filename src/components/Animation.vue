<template>
  <svg height="100vh" width="auto" viewBox="0 0 385 531" shape-rendering="geometricPrecision" text-rendering="geometricPrecision">
    <polygon v-for="polygon in polygons" :key="polygon"
      :points="convertPoints(polygon.data)"
      :fill="convertColor(polygon.color)" 
    />
  </svg>
</template>

<script>
import json from './polygons.json'
export default {
  name: 'Animation',
  data(){
    return{
      polygons: json,
      randomizedPolygons: [],
      windowWidth: window.screen.width,
      windowHeight: window.screen.height
    }
  },
  created: function () {

    this.randomizedPolygons = JSON.parse(JSON.stringify(this.polygons))
    for (var i = 0; i < this.randomizedPolygons.length; i++) {
      let data = this.randomizedPolygons[i]['data'].slice();

      let newX = this.randomInt(0,this.windowWidth)
      let newY = this.randomInt(0,this.windowHeight)
      this.randomizedPolygons[i]['data'][0] = newX
      this.randomizedPolygons[i]['data'][1] = newY

      this.randomizedPolygons[i]['data'][2] = newX+(data[2]-data[0])
      this.randomizedPolygons[i]['data'][3] = newY+(data[3]-data[1])

      newX = this.randomizedPolygons[i]['data'][2]
      newY = this.randomizedPolygons[i]['data'][3]

      this.randomizedPolygons[i]['data'][4] = newX+(data[4]-data[2])
      this.randomizedPolygons[i]['data'][5] = newY+(data[5]-data[3])
    }
  },
  methods: {
    randomInt: function(min, max) {
      return min + Math.floor((max - min) * Math.random());
    },
    convertPoints: function(data) {
      return data[0]+','+data[1]+' '+data[2]+','+data[3]+' '+data[4]+','+data[5]
    },
    convertColor: function(color) {
      return 'rgb('+color[0]+','+color[1]+','+color[2]+')'
    }
  },
  props: {
    msg: String
  }
}
</script>