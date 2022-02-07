<script setup>
import BottomBar from './components/BottomBar.vue'
import database from './data/database.js'
import Modal from './components/Modal.vue';
import Accordion from './components/Accordion.vue';
import QuarterSelection from './components/QuarterSelection.vue';
</script>

<template>
  <QuarterSelection></QuarterSelection>
</template>

<style>
html {
  background-color: #191929;
  margin: 0;
  padding: 0;
  color: rgb(170, 170, 170);
}

#app {
  font-family: Arial, Helvetica, sans-serif;
}

@media only screen and (min-device-width: 300px) and (max-device-width: 600px) {
  #app {
    display: flex;
    flex-direction: column-reverse;
    flex-wrap: nowrap;
    height: 85vh;
    justify-content: flex-start;
  }
}
</style>