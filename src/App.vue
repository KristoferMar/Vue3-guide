<template>
  <div id="app">
    <Header></Header>
    <mainview></mainview>
    <HelloWorld msg="Welcome to Your Vue.js + TypeScript App"/>
  </div>
</template>

<script lang="ts">
import { createComponent, ref } from '@vue/composition-api';
import { Component, Vue } from 'vue-property-decorator';
import HelloWorld from './components/HelloWorld.vue';
import Mainview from './views/mainview/Mainview.vue';
import Header from './components/Header.vue';

export default createComponent({
  setup() {
  },
  components: {
    HelloWorld,
    Mainview,
    Header,
  },
});
</script>

<style>

</style>
