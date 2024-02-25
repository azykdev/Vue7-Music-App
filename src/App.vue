<template>
  <div class="app-container p-3">
    <div class="display">
      <SongList />
    </div>
  </div>
</template>

<script>
import SongList from "./components/SongList.vue";

export default {
  name: "App",
  components: { SongList },
};
</script>

<style scoped>
.display {
  width: 350px;
  height: 700px;
  margin: 20px auto;
  background-color: rgb(245, 245, 245);
  border-radius: 10px;
  border: 10px solid #000000;
}
</style>
