<template>
  <div class="video-player-wrapper" ref="video_container">
    
    <video ref="player" class="player" :preload="preload" @timeupdate="updateProgress">
      <source :src="src" type="video/mp4">
    </video>
    <div class="controls theme-dark">
      <div class="play" @click="playPause">
        <font-awesome-icon icon="play" v-if="playIcon"/>
        <font-awesome-icon icon="pause" v-else/>
      </div>
      <div class="progressbar" @click="skipTo" ref="progress">
        <div class="progressbar_filled" ref="progress_filled"></div>
      </div>
      <div class="fullscreen" @click="fullscreen">
        <font-awesome-icon icon="expand" />
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'v-video',
    props: {
      src: {
        type: String,
        default: '',
      },
      cover: {
        type: String,
        default: '',
      },
      preload: {
        type: String,
        default: 'metadata',
      },
    },
    data() {
      return {
        playIcon: "►",
      }
    },
    methods: {
      playPause() {
        if (this.$refs.player.paused) {
          this.$refs.player.play();
          this.playIcon = false;        
        } else {
          this.$refs.player.pause();
          this.playIcon = true;
        }   
      },
      updateProgress(e) {
        const actualTime = (this.$refs.player.currentTime / this.$refs.player.duration) * 100;
        this.$refs.progress_filled.style.flexBasis = `${actualTime}%`;
        
      },
      skipTo(e) {
        const newTime = (e.offsetX / this.$refs.progress.offsetWidth) * this.$refs.player.duration;
        this.$refs.player.currentTime = newTime;
      },
      fullscreen() {
        const isFullscreen = document.fullscreenElement ||
        document.mozFullScreenElement ||
        document.webkitFullscreenElement ||
        document.msFullscreenElement;
        if (!isFullscreen) {          
          this.goFullscreen('video_container');
        } else {          
          this.exitFullscreen();
        }
      },
      goFullscreen(element) {
          if (this.$refs[element].requestFullscreen) {
            this.$refs[element].requestFullscreen();
          } else if (this.$refs[element].mozRequestFullScreen) {
            this.$refs[element].mozRequestFullScreen();
          } else if (this.$refs[element].webkitRequestFullscreen) {            
            this.$refs[element].webkitRequestFullscreen();
          } else if (this.$refs[element].msRequestFullscreen) { 
            this.$refs[element].msRequestFullscreen();
          }
      },
      exitFullscreen() {
        if (document.exitFullscreen) {
          document.exitFullscreen();
        } else if (document.mozCancelFullScreen) {
          document.mozCancelFullScreen();
        } else if (document.webkitExitFullscreen) {
          document.webkitExitFullscreen();
        }
      }
    },
    mounted() {
      console.log(this.$refs.player.currentTime, this.$refs.player.duration);
    }
  };
</script>

<style scoped>
  .video-player-wrapper {
    position: relative;
    padding: 0px;
    /* z-index: 1; */
  }
  .video-player-wrapper video {
    width: 100%;
    margin: 0px;
    padding: 0px;
  }

  video::-webkit-media-controls-enclosure {
    display:none !important;
  }

  .controls {
    position: absolute;
    margin: 0px;
    padding: 0px;
    left: 0px;
    right: 0px;
    display: flex;
    flex-wrap: nowrap;
    justify-content: center;
    align-items: stretch;
    flex-direction: row;
    bottom: 1vh;
    z-index: 2147483647 !important;
    width: 100%;
  }

  .play {
    cursor: pointer;
    padding: 10px;
    font-size: 1rem;
    flex: 5;
  }

  .progressbar {
    position: relative;
    flex: 90 auto;
    display: flex;
    flex-wrap: nowrap;
    justify-content: flex-start;
    align-items: stretch;
    flex-direction: row;
  }
  .progressbar_filled {
    flex: 0;
    width: 0%;
    flex-basis: 0%;
  }

  .fullscreen {
    cursor: pointer;
    padding: 10px;
    font-size: 1rem;
    flex: 5;
  }

  .theme-dark div {
    background-color: rgba(0 , 0, 0, 0.35);
    color: #d3d3d3;
  }

   .theme-dark .progressbar_filled {
      background-color: rgba(196, 196, 196, 0.7) !important;     
   }

   .theme-dark div:hover {
      background-color: rgba(0 , 0, 0, 0.65);     
   }
</style>