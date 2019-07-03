<template>
  <div id="app">
    <HelloWorld :track="track"/>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
var a = null;
export default {
  name: 'app',
  components: {
    HelloWorld
  },
  data() {
    return {
      tracks: {
        pointer: {
          x: 1,
          y: 1,
        },
        video: null,
      }
    }
  },
  computed: {
    track() {
      return this.tracks;
    }
  },
  mounted() {
    setInterval(() => {
      this.track.pointer.x += 1.1;
      // this.track.video = a;
    }, 100);
    const videoPlayer = document.getElementById("video-player") // this is a <video> element

function onSuccessWithSrcObject(stream) {
   videoPlayer.srcObject = stream;
}

function onSuccessWithSrc(stream) {
   videoPlayer.src = window.URL.createObjectURL(stream);
}

navigator.mediaDevices.getUserMedia({ audio: true, video: true })
  .then(stream => {
    // if ("srcObject" in videoPlayer) {
    //   onSuccessWithSrcObject(stream)
    // } else {
    //   onSuccessWithSrc(stream)
    // }
    // a = stream;
    this.tracks.video = stream;
  })
  }
}
</script>
