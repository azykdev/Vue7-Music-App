<template>
  <div v-if="!this.isPlayerVisible" class="song-list">
    <h3 class="header">
      <span class="cam"></span>
      Vue music app
    </h3>
    <ul class="p-4">
      <li
        v-for="(song, i) in song_list"
        :key="song.id"
        class="mb-4 cursor-pointer flex justify-between"
        @click="playSong(i)"
      >
        <img :src="song.src" alt="" class="w-2/12 rounded-lg" />
        <div class="w-9/12">
          <h6 class="font-semibold text-orange-500">{{ song.name }}</h6>
          <span class="text-slate-700 text-sm">{{ song.artistName }} - </span>
          <span class="text-slate-400 text-sm">{{ song.albumName }}</span>
        </div>
      </li>
    </ul>
  </div>
  <div v-else class="p-5">
    <SongPlayer
      :song="song_list[currentSongIndex]"
      @goBack="isPlayerVisible = !isPlayerVisible"
      @next="next"
      @previous="previous"
    />
  </div>
</template>

<script>
import SongPlayer from "./SongPlayer.vue";
export default {
  name: "SongList",
  components: {
    SongPlayer,
  },
  data() {
    return {
      isPlayerVisible: false,
      currentSongIndex: 0,
      song_list: [
        {
          id: 1,
          name: "Name 1",
          artistName: "Ar name 1",
          albumName: "Al name 1",
          year: 2023,
          src: "https://source.unsplash.com/random/400x400/?music=1",
          songSrc: "https://filesamples.com/samples/audio/mp3/sample1.mp3",
        },
        {
          id: 2,
          name: "Name 2",
          artistName: "Ar name 2",
          albumName: "Al name 2",
          year: 2023,
          src: "https://source.unsplash.com/random/400x400/?music=2",
          songSrc: "https://filesamples.com/samples/audio/mp3/sample2.mp3",
        },
        {
          id: 1,
          name: "Name 3",
          artistName: "Ar name 3",
          albumName: "Al name 3",
          year: 2023,
          src: "https://source.unsplash.com/random/400x400/?music=3",
          songSrc: "https://filesamples.com/samples/audio/mp3/sample3.mp3",
        },
      ],
    };
  },
  methods: {
    playSong(index) {
      this.currentSongIndex = index;
      this.isPlayerVisible = true;
    },
    next() {
      if (this.currentSongIndex < this.song_list.length - 1) {
        this.currentSongIndex++;
      } else {
        this.currentSongIndex = 0;
      }
    },
    previous() {
      if (this.currentSongIndex > 0) {
        this.currentSongIndex--;
      } else {
        this.currentSongIndex = this.song_list.length - 1;
      }
    },
  },
};
</script>

<style scoped>
.header {
  background-image: url("https://source.unsplash.com/random/400x400/?music/");
  background-position: center center;
  font-size: 40px;
  text-align: center;
  color: rgb(165, 165, 165);
  padding-bottom: 20px;
}
.cam {
  width: 30px;
  height: 25px;
  background: #000;
  display: block;
  margin: 0;
  padding: 0;
  border-radius: 0 0 50px 50px;
  margin: 0 auto;
}
</style>
