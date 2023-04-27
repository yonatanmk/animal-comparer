<template>
  <div>
    <h1>DEMO 1</h1>
    <div>{{ state.message }}</div>
    <button @click="incrementCounter">+</button>
    <button @click="decrementCounter">-</button>
    <div>Counter: {{ state.counter }}</div>
    <div>Prop: {{ msgProp }}</div>
    <div>Computed: {{ compMessage }}</div>
  </div>
</template>

<script lang="ts">
import { defineComponent, onMounted, onUpdated, onUnmounted, reactive, computed } from "vue";

export default defineComponent({
  props: {
    msgProp: {
      type: String,
      required: true
    }
  },
  setup(props) {
    const state = reactive({
      message: "Hello, World!",
      counter: 0
    });

    const incrementCounter = () => {
      state.counter++;
    };

    const decrementCounter = () => {
      state.counter--;
    };

    onMounted(() => {
      console.log("Component 1 mounted");
      console.log(props)
    });

    onUpdated(() => {
      console.log("Component 1 updated");
    });

    onUnmounted(() => {
      console.log("Component 1 destroyed");
    });

    const compMessage = computed(() => `${props.msgProp}---${state.counter}`)

    return { state, incrementCounter, decrementCounter, compMessage };
  }
});
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
