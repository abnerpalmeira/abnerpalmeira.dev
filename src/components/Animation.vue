<template>
  <svg v-on:click="animate" height="100vh" width="100%" viewBox="0 0 385 531" shape-rendering="geometricPrecision" text-rendering="geometricPrecision">
    <polygon 
      v-for="(polygon,index) in randomizedPolygons" :key="`polygon-${index}`"
      :points="convertPoints(polygon.data)"
      :fill="convertColor(polygon.color)"
      opacity="0.51"
      :id="`polygon-${index}`" 
    />
  </svg>
</template>

<script>

import {TimelineMax,Power4} from 'gsap'
import json from './polygons.json'

export default {
  name: 'Animation',
  data(){
    return{
      flag: false,
      polygons: json,
      randomizedPolygons: [],
      timeLine: new TimelineMax(),
      windowWidth: window.screen.width,
      windowHeight: window.screen.height
    }
  },
  created: function () {

    this.randomizedPolygons = JSON.parse(JSON.stringify(this.polygons))
    for (var i = 0; i < this.randomizedPolygons.length; i++) {

      let data = this.randomizedPolygons[i]['data'].slice();

      let newX = this.randomInt(-this.windowWidth*0.50,this.windowWidth)
      let newY = this.randomInt(-this.windowHeight*0.50,this.windowHeight)

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
    animate: function() {
      this.timeLine.pause()
      if(!this.flag){
        this.timeLine.resume()
        this.flag = true
        this.timeLine.add('T1')
        for (var i = 0; i < 50; i++) {
          this.timeLine.to(
            `#polygon-${i}`,
            0.5,
            {
              attr: {
                points: this.convertPoints(this.polygons[i]['data'])
              },
              ease:Power4.easeOut
            },'T1')
        }

        this.timeLine.add('T2')
        for (i = 50; i < 200; i++) {
          this.timeLine.to(
            `#polygon-${i}`,
            this.randomFloat(3,4),
            {
              attr: {
                points: this.convertPoints(this.polygons[i]['data'])
              },
              ease:Power4.easeOut
            },`T2+=${this.randomFloat(-2,4)}`)
        }

        this.timeLine.add('T3')
        for (i = 200; i < 500; i++) {
          this.timeLine.to(
            `#polygon-${i}`,
            this.randomFloat(2,8),
            {
              attr: {
                points: this.convertPoints(this.polygons[i]['data'])
              },
              ease:Power4.easeOut
            },`T3+=${this.randomFloat(-5,20)}`)
        }
      }
      else{
        this.flag = false
      }

      //alert('cliquei')
    },
    convertPoints: function(data) {
      return `${data[0]},${data[1]} ${data[2]},${data[3]} ${data[4]},${data[5]}`
    },
    convertColor: function(color) {
      return `rgb(${color[0]},${color[1]},${color[2]})`
    },
    randomInt: function(min, max) {
      return min + Math.floor((max - min) * Math.random());
    },
    randomFloat: function(min, max) {
      return min + (max - min) * Math.random();
    }
  },
  props: {
    msg: String
  }
}
</script>