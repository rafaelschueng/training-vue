<template>
  <div id="SearchBar" class="col">
    <form action="#" class="form-inline justify-content-center">
      <div class="input-group">
        <div class="input-group-prepend">
          <div class="input-group-text">O que é:</div>
        </div> 
        <input id="SearchField" class="form-control" type="text" :placeholder="'Pesquise com: '.concat(SearchEngine)" v-on:keyup="SearchEngineQuery" v-model="query">
        <div class="input-group-prepend">
          <div class="input-group-text">?</div>
        </div>
      </div>
    </form>
    <div id='SearchEngineResult' class="row justify-content-center">
      <div v-if="SearchEngineResultIcon" class="text-center">
        <img class="img-fluid" :src="SearchEngineResultIcon"/>  
      </div>
      <div v-if="SearchEngineResponse" class="col-sm-6 text-center">
        <p>{{SearchEngineResponse}}</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'SearchBar',
  props: {
    SearchEngine: String
  },
  data: function () {
    return { 
      query:'',
      SearchEngineResponse:'',
      SearchEngineResultIcon:''
    }
  },
  methods: {
    SearchEngineQuery: function () {
      fetch(`https://api.duckduckgo.com/?q=${this.query}&format=json`)
      .then((response) => response.json()) 
      .then((data) => {
        this.SearchEngineResponse = data.Abstract
        this.SearchEngineResultIcon = data.Results[0].Icon.URL
      })
    }
  }
}
</script>

<style>
#SearchBar {
  margin: 25vh 0 0 0;
}
#SearchEngineResult img {
  height: 30px;
}
#SearchField {
  width: 30vw;
}
#SearchBar form {
  margin-bottom: 20px;
}
</style>
