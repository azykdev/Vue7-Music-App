<template>
  <audio :src="song.songSrc" ref="audioPlayer" preload="auto" autoplay></audio>
  <div class="music-player">
    <div class="flex justify-between">
      <button class="btn" @click="goBack">Back</button>
      <span class="btn text-orange-500">VueJs music app</span>
    </div>

    <img :src="song.src" alt="" class="rounded-full my-8" />

    <div class="text-center">
      <p class="text-orange-500 font-semibold">{{ song.name }}</p>
      <p class="text-slate-700 text-sm">
        {{ song.artistName }} - {{ song.albumName }}
      </p>
      <p class="text-slate-400 text-sm">{{ song.year }}</p>
    </div>

    <div class="flex justify-around mt-20">
      <button class="btn" @click="previous">
        <i class="fa-solid fa-backward-step fa-2x"></i>
      </button>
      <button @click="playToggle" class="btn play">
        <i v-if="isPlaying" class="fa-solid fa-play fa-2x ms-1"></i>
        <i v-else class="fa-solid fa-pause fa-2x"></i>
      </button>
      <button class="btn" @click="next">
        <i class="fa-solid fa-forward-step fa-2x"></i>
      </button>
    </div>
  </div>
</template>

<script>
export default {
  name: "SongPlayer",
  data() {
    return {
      isPlaying: false,
    };
  },
  props: {
    song: {
      id: Number,
      name: String,
      artistName: String,
      albumName: String,
      year: Number,
      src: String,
      songSrc: String,
    },
  },
  emits: ["goBack", "next", "previous"],
  methods: {
    goBack() {
      this.$emit("goBack");
    },
    next() {
      this.$emit("next");
    },
    previous() {
      this.$emit("previous");
    },
    playToggle() {
      if (this.isPlaying) {
        this.$refs.audioPlayer.play();
      } else {
        this.$refs.audioPlayer.pause();
      }

      this.isPlaying = !this.isPlaying;
    },
  },
};
</script>

<style scoped>
.play {
  width: 70px;
  height: 70px;
  background: #ff712a;
  border-radius: 50%;
  text-align: center;
  color: #fff;
}
</style>
