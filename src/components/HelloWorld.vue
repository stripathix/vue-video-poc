<template>
  <div >
    {{t}}
    <video
      autoplay="autoplay"
      :srcObject.prop="trackStream"
      style="height: 300px; width: 300px" />
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    track: Object,
  },
  watch: {
    // whenever question changes, this function will run
    'track': {
      deep: true,
          handler (val, oldVal) {
            // do your stuff
            console.log("hbjk");
          }
    }
  },
  data() {
    return {
      t: 1,
    }
  },
  mounted() {
    setInterval(() => {
      this.t += 1;
    }, 3000)
  },
  computed: {
    trackStream() {
      // console.log("trackStream");
      var a = this.track ? this.track.video : new MediaStream();
      console.log(a);
      return a;
    },
    pointer() {
      // console.log("pointer");
      return this.track.pointer.x;// + this.track.video.id;
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
