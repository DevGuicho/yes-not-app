<template>
  <h2>{{ customTitle }}</h2>
  <p>{{ counter }}<sup>2</sup> = {{ getSquareValue }}</p>
  <div>
    <button v-on:click="decrease">-1</button>
    <button v-on:click="increase">+1</button>
  </div>
</template>

<script>
export default {
  name: "Counter",
  props: {
    title: String,
    start: {
      type: Number,
      default: 101,
      // required: true,
      validator(value) {
        return value > 100;
      },
    },
  },
  data() {
    return {
      counter: this.start,
    };
  },
  methods: {
    increase() {
      this.counter++;
    },
    decrease() {
      this.counter--;
    },
  },
  computed: {
    getSquareValue() {
      return this.counter * this.counter;
    },
    customTitle() {
      return this.title || "Counter";
    },
  },
};
</script>

<style>
button {
  background-color: #64bb87;
  border-radius: 5px;
  border: 1px solid white;
  color: white;
  cursor: pointer;
  margin: 0 5px;
  padding: 10px 16px;
}
button:hover {
  background-color: #5aa67b;
}
</style>
