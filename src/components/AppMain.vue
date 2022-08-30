<template>
    <div class="container-main">
        <div>
            <img src="" alt="">
        </div>
        <div>    
            <ul>
                <li v-for="info in MovieList" :key="info.id" :info="info">{{info.title}}</li>
            </ul>
        </div>
    </div>
</template>

<script>
import axios from 'axios';

export default {
    name: 'AppMain',

    data() {
        return {
            MovieList: [],
        }
    },
    created() {
        axios.get('https://api.themoviedb.org/3/search/movie?api_key=b897f127a3dbd85d52cd82ed32fa6440&query=2001&language=it-IT')
        .then((results) => {
          this.MovieList = results.data.results;
        })
        .catch((err) => {
          console.log(err);
        })
    }    
}
</script>

<style lang="scss">

</style>