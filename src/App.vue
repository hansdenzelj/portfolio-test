<script>
import Float from "./components/Float.vue";
import Banner from "./components/Banner.vue";
import CardContainer from "./components/CardContainer.vue";
import Card from "./components/Card.vue";
import Foot from "./components/Foot.vue";
import ProjectView from "./components/ProjectView.vue";

export default {
  components: {
    Float,
    Banner,
    CardContainer,
    Card,
    ProjectView,
    Foot,
  },
  data() {
    return {
      default_textcolor: "#FFFFFF",
      default_bgcolor: "#242424",
      bgcolor: "#242424",
      textcolor: "#FFFFFF",
    };
  },
  methods: {
    setTheme(color) {
      this.bgcolor = changeColor(color[0], -20);
      this.textcolor = color[1];
    },
    unsetTheme() {
      this.bgcolor = this.default_bgcolor;
      this.textcolor = this.default_textcolor;
    },
  },
};

//Function to darken colors, courtesy of:
//https://stackoverflow.com/questions/62515517/darken-and-lighten-colors-in-javascript

function changeColor(color, amount) {
  // #FFF not supportet rather use #FFFFFF
  const clamp = (val) => Math.min(Math.max(val, 0), 0xff);
  const fill = (str) => ("00" + str).slice(-2);

  const num = parseInt(color.substr(1), 16);
  const red = clamp((num >> 16) + amount);
  const green = clamp(((num >> 8) & 0x00ff) + amount);
  const blue = clamp((num & 0x0000ff) + amount);
  return (
    "#" +
    fill(red.toString(16)) +
    fill(green.toString(16)) +
    fill(blue.toString(16))
  );
}
</script>

<template>
  <div
    class="app-wrapper"
    :style="{ 'background-color': this.bgcolor, color: this.textcolor }"
  >
  <ProjectView />

    <header>
      <Banner />
    </header>

    <main>
      <section class="section-project">
        <h1>Projects [Solo & Group]</h1>
        <CardContainer>
          <Card
            @setColor="(color) => setTheme(color)"
            @unsetColor="unsetTheme()"
            :theme="{
              foreground: 'black',
              background: '#ffe4e1',
            }"
          >
            <template #title>Project</template>
            <template #image><img src="./assets/project_1.png" /></template>
          </Card>

          <Card
            @setColor="(color) => setTheme(color)"
            @unsetColor="unsetTheme()"
            :theme="{
              foreground: 'white',
              background: '#ec2c01',
            }"
          >
            <template #title>Project</template>
            <template #image>
              <img
                src="./assets/project_2.png"
                width="70%"
                style="align-self: center"
              />
            </template>
          </Card>

          <Card
            @setColor="(color) => setTheme(color)"
            @unsetColor="unsetTheme()"
            :theme="{
              foreground: 'white',
              background: '#027898',
            }"
          >
            <template #title>Project</template>
            <template #image>
              <img
                src="./assets/project_3.png"
                width="70%"
                style="align-self: flex-start"
              />
            </template>
          </Card>

          <Card
            @setColor="(color) => setTheme(color)"
            @unsetColor="unsetTheme()"
            :theme="{
              foreground: 'black',
              background: '#e6e4e0',
            }"
          >
            <template #title>Project</template>
            <template #image>
              <img
                src="./assets/project_4.png"
                width="100%"
                style="align-self: flex-start"
              />
            </template>
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
body > footer {
  position: sticky;
  top: 100vh;
}

main {
  padding: 0 1em 1em 1em;
}

span {
  font-size: clamp(1rem, 2.5vw, 2rem);
}

.app-wrapper {
  transition: background-color 250ms;
  min-height: 100vh;
}
</style>
