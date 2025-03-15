<script setup>
import { ref } from 'vue'
import Robot from './components/Robot.vue';
import Control from './components/Control.vue';

const isRobotActive = ref(true);
const top = ref(0);
const left = ref(0);
</script>

<template>

  <Control :is-robot-active="isRobotActive" v-model:x="left" v-model:y="top"></Control>
  <div class="field">
    <Robot :top="top" :left="left" v-model="isRobotActive"></Robot>
  </div>

</template>

<style scoped>
.field {
  position: relative;
  width: 100%;
  height: 75vh;
  padding: 1rem;
  margin: 1rem;
  border: thin dashed lightblue
}
</style>
