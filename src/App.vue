<template>
  <div id="app">
    <v_video src="VIDEO_URL"/>
  </div>
</template>

<script>
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
