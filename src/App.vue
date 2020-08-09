<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png" />

    <h1>MUSIC APP</h1>

    <h2>
      {{current.title}} -
      <span>{{current.artist}}</span>
    </h2>


    <button>Prev</button>
    <button>Pause</button>
    <button>play</button>

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
          src:require("./assets/Terri-Ojoro.mp3") 
        }
      ],
      player: new Audio()
    };
  },

  created() {
    this.current = this.songs[0];
    this.player.src = this.current.src;
    this.player.play();
  },
  components: {}
};
</script>

<style>

*{
  margin:0;
  padding:0
}
body{

margin:auto
}
button{

  margin:10px;
}
</style>
