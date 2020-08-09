<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png" />

    <h1>MUSIC APP</h1>

    <h2>
      {{current.title}} -
      <span>{{current.artist}}</span>
    </h2>

    <button>Prev</button>
    <button v-if="!isNowPlaying" @click="pause()">Pause</button>
    <button v-else @click="play()">play</button>

    <button>Next</button>
  </div>
</template>

<script>
export default {
  name: "App",

  data() {
    return {
      index: 0,
      current: {},

      songs: [
        {
          title: "billonaire",
          artist: "Teni",
          src: require("./assets/Teni-Billionaire.mp3")
        },

        {
          title: "ojoro",
          artist: "Terri",
          src: require("./assets/Terri-Ojoro.mp3")
        }
      ],
      player: new Audio(),
      isNowPlaying: true,
      song: null
    };
  },

  created() {
    this.current = this.songs[this.index];
    this.player.src = this.current.src;
  },
  components: {},
  methods: {
    play(song) {
      if ( typeof song.src != "undefined") {
        this.current = song;
        this.player.src = this.current.src;
      }
      this.player.play();
      this.isNowPlaying = false;
    },

    pause() {
      this.player.pause();
      this.isNowPlaying = true;
    }
  }
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
}
body {
  margin: auto;
}
button {
  margin: 10px;
}
</style>
