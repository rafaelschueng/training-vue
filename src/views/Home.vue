<template>
  <div class="home">
    <div class="row" id="top"></div>
    <div class="row" id="middle">
      <SearchBar SearchEngine='API do DuckDuckGo'/>
    </div>
    <div class="row" id="bottom"></div>
  </div>
</template>

<script>
// @ is an alias to /src
import SearchBar from '@/components/SearchBar.vue'

export default {
  name: 'Home',
  components: {
    SearchBar
  }
}
</script>

<style>
#middle {
  height: 100vh;
}

#bottom {
  position: absolute;
  height: 25vh;
  width: 100vw;
  bottom: 0;
}
</style>
