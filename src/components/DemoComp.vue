<template>
  <div>
    <h1>DEMO 1</h1>
    <div>{{ state.message }}</div>
    <button @click="incrementCounter">+</button>
    <div>Counter: {{ state.counter }}</div>
    <div>Prop: {{ msgProp }}</div>
  </div>
</template>

<script lang="ts">
import { defineProps, onMounted, onUpdated, onUnmounted, reactive } from "vue";

interface IDemoProps {
  msgProp: string;
}

export default {
  props: {
    msgProp: {
      type: String,
      required: true
    }
  },
  // props: ['msgProp'],
  setup(props: any) {
    const typedProps = defineProps<any>({
      msgProp: props.msgProp,
    });


    console.log(props)
    console.log(typedProps)

    const state = reactive({
      message: "Hello, World!",
      counter: 0
    });

    const incrementCounter = () => {
      state.counter++;
    };

    onMounted(() => {
      console.log("Component mounted");
      console.log(props)
      console.log(typedProps)
    });

    onUpdated(() => {
      console.log("Component updated");
    });

    onUnmounted(() => {
      console.log("Component destroyed");
    });

    return { state, incrementCounter };
  }
};
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
