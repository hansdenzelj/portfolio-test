<script>
export default {
  props: {
    theme: {
      type: Object,
      default: () => ({
        foreground: "#000000",
        background: "#FFFFFF",
      }),
    },
    active: {
      type: Boolean,
      default: false,
    },
    project_id: Number,
  },
  data() {
    return {
      textcolor: "#000000",
      bgcolor: "#ffffff",
    };
  },
  emits: ["close"],
  methods: {
    closeView() {
      if ((self.active = true)) {
        self.active = false;
      }
    },
    getProject(id) {
      switch (id) {
        case 1:
          return {
            title: "hi",
            description: "project",
          };
      }
    },
  },
  watch: {
    theme(color) {
      this.textcolor = color.foreground;
      this.bgcolor = color.background;
    },
  },
};
</script>

<template>
  <div v-if="active" class="Project-Wrapper" @click="$emit('close')">
    <div
      class="Project"
      :style="{ 'background-color': this.bgcolor, color: this.textcolor }"
    >
      <h1>{{ getProject(1)["description"] }}</h1>
      <p :style="{ color: this.textcolor }">{{ getProject(1)["title"] }}</p>
    </div>
  </div>
</template>

<style scoped>
.Project-Wrapper {
  background-color: rgba(0, 0, 0, 0.85);
  position: fixed;
  z-index: 998;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;

  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

.Project {
  z-index: 999;
  width: 80%;
  height: 50%;
  background-color: white;
  border-radius: 0.75em;
  padding: 1em;
}

p {
  color: #000;
  margin: 0;
}

@media (min-width: 768px) {
  .Project {
    width: 80%;
  }
}

@media (min-width: 1536px) {
  .Project {
    width: 70%;
  }
}

@media (min-width: 1920px) {
  .Project {
    width: 60%;
  }
}

@media (min-width: 2560px) {
  .Project {
    width: 50%;
  }
}

@media (min-width: 3440px) {
  .Project {
    width: 40%;
  }
}
</style>
