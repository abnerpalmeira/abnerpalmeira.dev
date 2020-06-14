<template>
  <svg v-on:click="triggerAnimation" height="100vh" width="100%" viewBox="0 0 385 531" shape-rendering="geometricPrecision" text-rendering="geometricPrecision">
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
    triggerAnimation: function() {
      if(!this.flag){
        this.timeLine.clear()
        this.timeLine.resume()
        this.flag = true
        this.timeLine.add(this.animate(0,50,'T1',this.polygons,0.5,0.5,0,0))
        this.timeLine.add(this.animate(50,200,'T2',this.polygons,3,4,-2,4))
        this.timeLine.add(this.animate(200,500,'T3',this.polygons,2,8,-10,20))
      }
      else{
        this.flag = false
        this.timeLine.clear()
        this.timeLine.resume()
        this.timeLine.add(this.animate(0,500,'T1',this.randomizedPolygons,0.5,0.5,0,0))
      }
    },
    animate: function(start,end,stage,polygons,durationStart,durationEnd,offsetStart,offsetEnd){
      
      var newTimeLine =  new TimelineMax()

      newTimeLine.add(stage)
      
      for (var i = start; i < end; i++) {
        this.timeLine.to(
          `#polygon-${i}`,
          this.randomFloat(durationStart,durationEnd),
          {
            attr: {
              points: this.convertPoints(polygons[i]['data'])
            },
            ease:Power4.easeOut
          },`${stage}+=${this.randomFloat(offsetStart,offsetEnd)}`)
      }

      return newTimeLine
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