<template>
  <div>
    <svg v-on:click="triggerAnimation" height="100vh" width="100%" x="0" y="0" viewBox="0 0 385 531" shape-rendering="geometricPrecision" text-rendering="geometricPrecision" xml:space="preserve">
      <polygon 
        v-for="(polygon,index) in randomizedPolygons" :key="`polygon-${index}`"
        :points="convertPoints(polygon.data)"
        :fill="convertColor(polygon.color)"
        opacity="0.51"
        :id="`polygon-${index}`"
      />

      <text x="192" y="265" id="text" fill="rgb(255,255,255)"  dominant-baseline="middle" text-anchor="middle">{{deviceType?'TAP':'CLICK'}} ON THE SCREEN</text>
      <svg x="192" y="395">
        <g class="expand" id="logo-linkedin" transform="scale(0.05)" opacity="0" @click.stop=''>
          <a xlink:href="https://www.linkedin.com/in/abner-samuel-193703125/" target="_blank">
          <path fill="rgb(255,255,255)" xmlns="http://www.w3.org/2000/svg" d="m475.074219 0h-438.148438c-20.394531 0-36.925781 16.53125-36.925781 36.925781v438.148438c0 20.394531 16.53125 36.925781 36.925781 36.925781h438.148438c20.394531 0 36.925781-16.53125 36.925781-36.925781v-438.148438c0-20.394531-16.53125-36.925781-36.925781-36.925781zm-293.464844 387h-62.347656v-187.574219h62.347656zm-31.171875-213.1875h-.40625c-20.921875 0-34.453125-14.402344-34.453125-32.402344 0-18.40625 13.945313-32.410156 35.273437-32.410156 21.328126 0 34.453126 14.003906 34.859376 32.410156 0 18-13.53125 32.402344-35.273438 32.402344zm255.984375 213.1875h-62.339844v-100.347656c0-25.21875-9.027343-42.417969-31.585937-42.417969-17.222656 0-27.480469 11.601563-31.988282 22.800781-1.648437 4.007813-2.050781 9.609375-2.050781 15.214844v104.75h-62.34375s.816407-169.976562 0-187.574219h62.34375v26.558594c8.285157-12.78125 23.109375-30.960937 56.1875-30.960937 41.019531 0 71.777344 26.808593 71.777344 84.421874zm0 0"/>
          </a>
        </g>
    </svg>
    <svg x="142" y="395">
      <g class="expand" id="logo-git" transform="scale(0.05)"  opacity="0" @click.stop=''>
        <a xlink:href="https://github.com/abnerpalmeira" target="_blank">
          <path xmlns="http://www.w3.org/2000/svg" fill="rgb(255,255,255)" d="M409.132,114.573c-19.608-33.596-46.205-60.194-79.798-79.8C295.736,15.166,259.057,5.365,219.271,5.365   c-39.781,0-76.472,9.804-110.063,29.408c-33.596,19.605-60.192,46.204-79.8,79.8C9.803,148.168,0,184.854,0,224.63   c0,47.78,13.94,90.745,41.827,128.906c27.884,38.164,63.906,64.572,108.063,79.227c5.14,0.954,8.945,0.283,11.419-1.996   c2.475-2.282,3.711-5.14,3.711-8.562c0-0.571-0.049-5.708-0.144-15.417c-0.098-9.709-0.144-18.179-0.144-25.406l-6.567,1.136   c-4.187,0.767-9.469,1.092-15.846,1c-6.374-0.089-12.991-0.757-19.842-1.999c-6.854-1.231-13.229-4.086-19.13-8.559   c-5.898-4.473-10.085-10.328-12.56-17.556l-2.855-6.57c-1.903-4.374-4.899-9.233-8.992-14.559   c-4.093-5.331-8.232-8.945-12.419-10.848l-1.999-1.431c-1.332-0.951-2.568-2.098-3.711-3.429c-1.142-1.331-1.997-2.663-2.568-3.997   c-0.572-1.335-0.098-2.43,1.427-3.289c1.525-0.859,4.281-1.276,8.28-1.276l5.708,0.853c3.807,0.763,8.516,3.042,14.133,6.851   c5.614,3.806,10.229,8.754,13.846,14.842c4.38,7.806,9.657,13.754,15.846,17.847c6.184,4.093,12.419,6.136,18.699,6.136   c6.28,0,11.704-0.476,16.274-1.423c4.565-0.952,8.848-2.383,12.847-4.285c1.713-12.758,6.377-22.559,13.988-29.41   c-10.848-1.14-20.601-2.857-29.264-5.14c-8.658-2.286-17.605-5.996-26.835-11.14c-9.235-5.137-16.896-11.516-22.985-19.126   c-6.09-7.614-11.088-17.61-14.987-29.979c-3.901-12.374-5.852-26.648-5.852-42.826c0-23.035,7.52-42.637,22.557-58.817   c-7.044-17.318-6.379-36.732,1.997-58.24c5.52-1.715,13.706-0.428,24.554,3.853c10.85,4.283,18.794,7.952,23.84,10.994   c5.046,3.041,9.089,5.618,12.135,7.708c17.705-4.947,35.976-7.421,54.818-7.421s37.117,2.474,54.823,7.421l10.849-6.849   c7.419-4.57,16.18-8.758,26.262-12.565c10.088-3.805,17.802-4.853,23.134-3.138c8.562,21.509,9.325,40.922,2.279,58.24   c15.036,16.18,22.559,35.787,22.559,58.817c0,16.178-1.958,30.497-5.853,42.966c-3.9,12.471-8.941,22.457-15.125,29.979   c-6.191,7.521-13.901,13.85-23.131,18.986c-9.232,5.14-18.182,8.85-26.84,11.136c-8.662,2.286-18.415,4.004-29.263,5.146   c9.894,8.562,14.842,22.077,14.842,40.539v60.237c0,3.422,1.19,6.279,3.572,8.562c2.379,2.279,6.136,2.95,11.276,1.995   c44.163-14.653,80.185-41.062,108.068-79.226c27.88-38.161,41.825-81.126,41.825-128.906   C438.536,184.851,428.728,148.168,409.132,114.573z"/>
        </a>
    </g>
    </svg>
    <svg x="242" y="395">
      <g class="expand" id="logo-twitter" transform="scale(0.05)"  opacity="0" @click.stop=''>
        <a xlink:href="https://twitter.com/abnerpalmeira" target="_blank">
          <path xmlns="http://www.w3.org/2000/svg" fill="rgb(255,255,255)"  d="M512,97.248c-19.04,8.352-39.328,13.888-60.48,16.576c21.76-12.992,38.368-33.408,46.176-58.016    c-20.288,12.096-42.688,20.64-66.56,25.408C411.872,60.704,384.416,48,354.464,48c-58.112,0-104.896,47.168-104.896,104.992    c0,8.32,0.704,16.32,2.432,23.936c-87.264-4.256-164.48-46.08-216.352-109.792c-9.056,15.712-14.368,33.696-14.368,53.056    c0,36.352,18.72,68.576,46.624,87.232c-16.864-0.32-33.408-5.216-47.424-12.928c0,0.32,0,0.736,0,1.152    c0,51.008,36.384,93.376,84.096,103.136c-8.544,2.336-17.856,3.456-27.52,3.456c-6.72,0-13.504-0.384-19.872-1.792    c13.6,41.568,52.192,72.128,98.08,73.12c-35.712,27.936-81.056,44.768-130.144,44.768c-8.608,0-16.864-0.384-25.12-1.44    C46.496,446.88,101.6,464,161.024,464c193.152,0,298.752-160,298.752-298.688c0-4.64-0.16-9.12-0.384-13.568    C480.224,136.96,497.728,118.496,512,97.248z"/>
        </a>
      </g>
    </svg>
  </svg>
  </div>
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
      deviceType: "ontouchstart" in document.documentElement,
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
        this.timeLine.set('#text',{autoAlpha:0},'T0')
        this.timeLine.add(this.animate(0,50,'T1',this.polygons,0.5,0.5,0,0))
        this.timeLine.add(this.animate(50,200,'T2',this.polygons,3,4,-2,4))
        this.timeLine.add(this.animate(200,499,'T3',this.polygons,2,8,-10,0))
        this.timeLine.set('#logo-git',{autoAlpha:1},'T3-=3')
        this.timeLine.set('#logo-linkedin',{autoAlpha:1},'T3-=3')
        this.timeLine.set('#logo-twitter',{autoAlpha:1},'T3-=3')
      }
      else{
        this.flag = false
        this.timeLine.clear()
        this.timeLine.resume()
        this.timeLine.add('T1')
        this.timeLine.set('#logo-git',{autoAlpha:0},'T0')
        this.timeLine.set('#logo-linkedin',{autoAlpha:0},'T0')
        this.timeLine.set('#logo-twitter',{autoAlpha:0},'T0')
        this.timeLine.set('#text',{autoAlpha:1},'T0')
        this.timeLine.add(this.animate(0,499,'T1',this.randomizedPolygons,1,2,0,0))
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
<style type="text/css">
  @import url('https://fonts.googleapis.com/css2?family=Roboto:wght@500&display=swap');
  a {
    text-decoration: none;
  }
  text{
    font-size:25px;
    font-family: 'Roboto', sans-serif;
  }
  .expand:hover{
      
  }
</style>