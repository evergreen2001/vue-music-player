<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png" />

    <h1>MUSIC APP</h1>

    <h2>
      {{current.title}} -
      <span>{{current.artist}}</span>
    </h2>

    <button @click="prev">Prev</button>
    <button v-if="!isNowPlaying" @click="pause">Pause</button>
    <button v-else @click="play">play</button>

    <button @click="next">Next</button>

    <section>
      <h3>{{username}} PLaylist</h3>



      <button v-for="song in songs" :key="song.src" @click="play(song)"> {{song.artist}}  || {{song.title}}</button>
    </section>
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
      username: ""
    };
  },

  created() {
    // this.username = prompt("enter your name ");

    // console.log(this.username);
    this.current = this.songs[this.index];
    this.player.src = this.current.src;
  },
  components: {},
  methods: {
    play(song) {
      if (typeof song.src != "undefined") {
        this.current = song;
        this.player.src = this.current.src;

     
      }
         this.player.play();
      this.isNowPlaying = false;
    },

    pause() {
      this.player.pause();
      this.isNowPlaying = true;
    } , 

    next(){

this.index++
      if(this.index > this.songs.length - 1){
        this.index = 0

      }

      this.current  = this.songs[this.index] ; 
      this.play(this.current)
    } , 

     prev(){

    this.index --;
      if(this.index < 0){
        this.index = this.songs.length -1

      }

      this.current  = this.songs[this.index] ; 
      this.play(this.current)
    
  }
  } , 
 
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
