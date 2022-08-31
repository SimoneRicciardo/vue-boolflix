<template>
  <div id="app">

    <AppHeader @search="getSearchMovie"/>
    <AppMain :MovieList="MovieList"/>

  </div>
</template>

<script>
import AppHeader from './components/AppHeader.vue';
import AppMain from './components/AppMain.vue';
import axios from 'axios';

export default {
  name: 'App',
  components: {
    AppHeader,
    AppMain
  },

  data(){
    return{
      MovieList: []
    }
  },

  methods: {
    getSearchMovie(text){
      axios.get('https://api.themoviedb.org/3/search/movie?api_key=b897f127a3dbd85d52cd82ed32fa6440&query=' + text + '&language=it-IT')
      .then(res=> {
        this.MovieList = res.data.results;
        console.log(this.MovieList)
      })
      .catch(err => {
        console.log(err)
      })
    }
  }
}
</script>

<style lang="scss">
  @import './Style/GenericRule.scss';

</style>
