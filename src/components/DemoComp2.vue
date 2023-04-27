<template>
  <div>
    <h1>DEMO 2</h1>
    <div>Prop: {{title}}</div>
    <div>Prop: {{msgProp}}</div>
  </div>
</template>

<script lang="ts">
import { defineComponent, onMounted } from "vue";

export default defineComponent({
  props: {
    title: {
      type: String,
      required: true,
    },
    msgProp: {
      type: String,
      required: true,
    }
  },
  setup(props) {
    onMounted(() => {
      console.log("Component mounted");
      console.log({
        props,
        title: props.title,
        msgProp: props.msgProp
      })
    });
  }
});
</script>
