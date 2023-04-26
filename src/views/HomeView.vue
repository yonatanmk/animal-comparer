<template>
  <div class="home">
    <DemoComp msgProp="Welcome to Your Vue.js + TypeScript App"/>
    <!-- <DemoComp /> -->
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import DemoComp from '@/components/DemoComp.vue';

export default defineComponent({
  name: 'HomeView',
  components: {
    DemoComp,
  },
});
</script>
