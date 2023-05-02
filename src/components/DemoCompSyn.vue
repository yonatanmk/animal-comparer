<template>
  <div>
    <h1>DEMO 3</h1>
    <div>{{ message }}</div>
    <button @click="incrementCounter">+</button>
    <button @click="decrementCounter">-</button>
    <div>Counter: {{ counter }}</div>
    <div>Prop: {{ msgProp }}</div>
    <div>Computed: {{ compMessage }}</div>
  </div>
</template>

<script lang="ts" setup>
import { defineProps, onMounted, onUpdated, onUnmounted, ref, computed } from "vue";

interface IDemoProps {
  msgProp: string;
}

// const props = defineProps({
//   msgProp: String
// })
const props = defineProps<IDemoProps>();

const message = ref("Hello, World!")
const counter = ref(0)

onMounted(() => {
  console.log("Component 3 mounted");
  console.log(props)
});

onUpdated(() => {
  console.log("Component 3 updated");
});

onUnmounted(() => {
  console.log("Component 3 destroyed");
});

const incrementCounter = () => {
  counter.value++;
};

const decrementCounter = () => {
  counter.value--;
};

const compMessage = computed(() => `${props.msgProp}---${counter.value}`)
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
