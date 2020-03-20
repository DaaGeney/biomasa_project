<template>
  <v-layout column justify-center align-center>
    <v-parallax id="parallax-hero" :src="images.background">
      <v-row no-gutters align="center" justify="center">
        <v-col class="text-center" cols="2" align-self="start"></v-col>
        <v-col class="text-center" cols="8" align-self="center">
          <v-sheet elevation="12" class="pa-2">
            <br />
            <v-img
              :src="images.logo"
              aspect-ratio="631.277"
              min-height="30vh"
              contain
            ></v-img>
            <h4 class="light--text font-weight-light text-center py-1">
              Portal para la sistematización de datos <br />
              sobre el potencial energético de la biomasa residual y <br />
              sus tecnologías de aprovechamiento.
            </h4>
            <div class="container">
              <div
                class="arrow"
                @click="$vuetify.goTo(selector[0], options)"
              ></div>
            </div>
            <br />
          </v-sheet>
        </v-col>
        <v-col class="text-center" cols="2" align-self="start"></v-col>
        <v-spacer></v-spacer>
      </v-row>
    </v-parallax>
    <div style="width:135%" id="first">
      <v-carousel
        style="margin-top: 15vh; padding-right: 10%; padding-left: 10%;"
        cycle
        height="530"
        hide-delimiter-background
        hide-delimiters
      >
        <v-carousel-item v-for="slide in slides" :key="slide.id">
          <v-sheet :color="slide.color" height="100%" class="pa-10">
            <v-row class="fill-height" align="center" justify="center">
              <div
                class="font-weight-bold pa-2"
                :class="{
                  'display-1': $vuetify.breakpoint.smAndDown,
                  'display-4': $vuetify.breakpoint.mdAndUp
                }"
              >
                {{ slide.tittle }}
              </div>
              <div
                class="light--text headline font-weight-light text-center mx-12"
              >
                {{ slide.description }}
              </div>
              <v-spacer></v-spacer>
              <v-spacer></v-spacer>
            </v-row>
          </v-sheet>
        </v-carousel-item>
      </v-carousel>
      <div class="container">
        <div
          class="arrow"
          @click="$vuetify.goTo(selector[1], options)"
          style="margin-bottom: 8vh;"
        ></div>
      </div>
    </div>
    <div style="width:135%" id="seccond">
      <v-col>
        <v-row style="margin-top: 15vh; padding-right: 10%; padding-left: 10%;">
          <v-col
            v-for="n in news"
            :key="n.id"
            class="text-center pa-12"
            cols="4"
          >
            <v-card
              raised
              align="justify"
              justify="justify"
            >
              <v-card-title>{{ n.tittle }}</v-card-title>
              <v-card-subtitle>{{ n.autor }}</v-card-subtitle>
              <v-card-text>{{ n.description }}</v-card-text>
            </v-card>
          </v-col>
        </v-row>
        <v-row>
          <v-col cols="12" justify="center" align-self="center">
            <div class="container">
              <div
                class="arrow"
                @click="$vuetify.goTo(selector[0], options)"
              ></div>
            </div>
          </v-col>
        </v-row>
      </v-col>
    </div>
  </v-layout>
</template>

<script>
import * as easings from 'vuetify/es5/services/goto/easing-patterns'
import config from '../assets/config.js'
let background_plant = config.routes.background_plant
let background_news = config.routes.background_wood

export default {
  data() {
    return {
      images: {
        logo: config.routes.logo,
        background: config.routes.background_main
      },
      news: config.news,
      slides: config.atributes,
      //Button Programatic Scroll
      type: 'selector',
      selector: ['#first', '#seccond'],
      selections: ['#first', '#second', '#third'],
      duration: 2000,
      offset: 0,
      easing: 'easeInOutCubic',
      easings: Object.keys(easings)
    }
  },
  mounted() {
    ;(document.getElementById('parallax-hero').style.width = '135%'),
      (document.getElementById('parallax-hero').style.height = '100vh'),
      (document.getElementById('first').style.backgroundImage =
        'url(' + background_plant + ')'),
      (document.getElementById('seccond').style.backgroundImage =
        'url(' + background_news + ')')
  },
  computed: {
    target() {
      const value = this[this.type]
      if (!isNaN(value)) return Number(value)
      else return value
    },
    options() {
      return {
        duration: this.duration,
        offset: this.offset,
        easing: this.easing
      }
    }
  }
}
</script>

<style scoped>
#first, #seccond {
  height: 100%;

  background-position: center;
  background-repeat: no-repeat;
  background-size: cover;
}
.arrow {
  box-sizing: border-box;
  height: 5vw;
  width: 5vw;
  border-style: solid;
  border-color: black;
  border-width: 0px 1px 1px 0px;
  transform: rotate(45deg);
  transition: border-width 150ms ease-in-out;
}

.arrow:hover {
  border-bottom-width: 4px;
  border-right-width: 4px;
}

.container {
  display: flex;
  align-items: center;
  justify-content: center;
}
</style>
