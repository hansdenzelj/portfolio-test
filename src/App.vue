<script>
import Float from './components/Float.vue'
import Banner from './components/Banner.vue'
import CardContainer from './components/CardContainer.vue'
import Card from './components/Card.vue'
import Foot from './components/Foot.vue'

export default {
  components: {
    Float,
    Banner,
    CardContainer,
    Card,    
    Foot,
  },
  data() {
    return {
      default_bgcolor: '#242424',
      bgcolor: '#242424'
    }
  },
  methods: {
    setBgColor(color) {
      this.bgcolor = color
    },
    unsetBgColor() {
      this.bgcolor = this.default_bgcolor
    }
  }
}
</script>

<template>
  <div class="app-wrapper" :style="{'background-color': this.bgcolor}">
    <Float></Float>

    <header>
      <Banner />
    </header>

    <main>
      <section class="section-project">
        <h1>Projects [Solo & Group]</h1>
          <CardContainer>

            <Card 
            @setColor="(color) => setBgColor(color)"
            @unsetColor="unsetBgColor()"
            :theme="{
              foreground: 'black',
              background: '#ffe4e1'
            }" >
            <span>Dessert Ordering Website</span>
            <span>Plain HTML, JS, JQuery</span>
            <br>
            <img src="./assets/project_1.png" />
            </Card>

            <Card 
            @setColor="(color) => setBgColor(color)"
            @unsetColor="unsetBgColor()"
            :theme="{
              foreground: 'white',
              background: '#ec2c01'
            }">
            <span>Car Renting Site</span>
            <span>HTML, JS, PHP</span>
            <br>
            <img src="./assets/project_2.png" width="70%" style="align-self: center;"/>
            </Card>

            <Card 
            @setColor="(color) => setBgColor(color)"
            @unsetColor="unsetBgColor()"
            :theme="{
              foreground: 'white',
              background: '#027898'
            }">
            <span>Task Manager Site</span>
            <span>React, Firebase</span>
            <span style="font-size: clamp(0.5rem, 2.5vw, 0.8rem);">Worked on database connectivity</span>
            <br>
            <img src="./assets/project_3.png" width="70%" style="align-self: center;"/>
            </Card>

            <Card 
            @setColor="(color) => setBgColor(color)"
            @unsetColor="unsetBgColor()"
            :theme="{
              foreground: 'black',
              background: '#e6e4e0'
            }">
            <span>Computer Vision Yoga App (WIP)</span>
            <span>Kivy, OpenCV, Tensorflow, MediaPipe</span>
            <span style="font-size: clamp(0.5rem, 2.5vw, 0.8rem);">
            Made a machine learning model to detect if the user is doing a Yoga pose<br>
            Added functions such as camera selection and timer
            </span>
            <br>
            <img src="./assets/project_4.png" width="100%" style="align-self: center;"/>
            </Card>

          </CardContainer>
      </section>
    </main>

    <footer>
      <Foot />
    </footer>

  </div>
</template>

<style scoped>
main {
  padding: 0 1em 1em 1em;
  height: 100%;
}

span {
  font-size: clamp(1rem, 2.5vw, 2rem);
}

.app-wrapper {
  transition: background-color 250ms;
  height: auto;
}
</style>