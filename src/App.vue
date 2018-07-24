<template>
  <div id="app">
    <v_video src="https://thiagodella.github.io/static/media/lunar_module.57ff26e.mp4"/>
  </div>
</template>

<script>/* eslint-disable camelcase */
import v_video from './components/v-video';

export default {
  name: 'App',
  components: {
    v_video,
  },
};
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
