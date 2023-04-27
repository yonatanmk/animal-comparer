<template>
  <div class="home">
    <DemoComp msgProp="Welcome to Your Vue.js + TypeScript App"/>
    <DemoComp2 title="Welcome to Your Vue.js + TypeScript App" msg-prop="msgProp"/>
    <!-- <DemoComp /> -->
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import DemoComp from '@/components/DemoComp.vue';
import DemoComp2 from '@/components/DemoComp2.vue';

export default defineComponent({
  name: 'HomeView',
  components: {
    DemoComp,
    DemoComp2,
  },
});
</script>
