<template>
  <div class="demo">
    <DemoComp msgProp="MESSAGE"/>
    <DemoComp2 title="MESSAGE" msg-prop="msgProp"/>
    <DemoCompSyn msgProp="MESSAGE"/>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import DemoComp from '@/components/DemoComp.vue';
import DemoComp2 from '@/components/DemoComp2.vue';
import DemoCompSyn from '@/components/DemoCompSyn.vue';

export default defineComponent({
  name: 'DemoView',
  components: {
    DemoComp,
    DemoComp2,
    DemoCompSyn,
  },
});
</script>
