<template>
  <img v-if="img" :src="img" alt="" />
  <div class="bg-dark"></div>
  <div class="indecision-container">
    <input
      type="text"
      v-model.trim="question"
      placeholder="Hazme una pregunta"
    />
    <p>Recuerda terminar con un singno de interrogación</p>
    <div v-if="answer">
      <h2>{{ question }}</h2>
      <h1>{{ answer }}</h1>
    </div>
  </div>
</template>

<script>
export default {
  name: "Indecision",
  data() {
    return {
      question: "",
      answer: null,
      img: null,
    };
  },
  methods: {
    async getAnswer() {
      this.answer = "Pensando ...";
      const res = await fetch("https://yesno.wtf/api");
      const data = await res.json();
      this.answer = data.answer === "yes" ? "Si" : "No";
      this.img = data.image;
    },
  },
  watch: {
    question(value, oldValue) {
      if (value.includes("?")) {
        this.getAnswer();
      }
    },
  },
};
</script>

<style scoped>
img,
.bg-dark {
  height: 100vh;
  left: 0px;
  max-height: 100%;
  max-width: 100%;
  position: fixed;
  top: 0px;
  width: 100vw;
}

.bg-dark {
  background-color: rgba(0, 0, 0, 0.4);
}

.indecision-container {
  position: relative;
  z-index: 99;
}

input {
  width: 250px;
  padding: 10px 15px;
  border-radius: 5px;
  border: none;
}
input:focus {
  outline: none;
}

p {
  color: white;
  font-size: 20px;
  margin-top: 0px;
}

h1,
h2 {
  color: white;
}

h2 {
  margin-top: 150px;
}
</style>
