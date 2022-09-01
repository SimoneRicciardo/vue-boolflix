<template>
    <div class="container-main">

        <div class="movie">
            <div>    

                <ul class="card">

                    <li v-for="(movie, index) in MovieList" :key="index">

                        <img :src="'https://image.tmdb.org/t/p/w342' + movie.poster_path " :alt="movie.title">

                        <!-- {{movie.title}}-
                        {{movie.original_title}}-
                        <img v-if="flags.includes(movie.original_language)" :src='"../assets/images/" + movie.original_language + ".png"'>
                        <span v-else>{{movie.original_language}}</span> -
                        {{movie.vote_average}}- -->

                    </li>

                </ul>

            </div>
        </div>

        <!-- <hr> -->

        <!-- <div class="tv">
            <div class="card">    
                <ul>
                    <li v-for="(tv, index) in TvList" :key="index">
                        <img :src="'https://image.tmdb.org/t/p/w342' + tv.poster_path " :alt="tv.name">
                        {{tv.name}}-
                        {{tv.original_name}}-
                        <img v-if="flags.includes(tv.original_language)" :src='"../assets/images/" + tv.original_language + ".png"'>
                        <span v-else>{{tv.original_language}}</span> -
                        {{tv.vote_average}}-
                        <i v-for="n in 5" class="fa-star" :class="(n >= getVote(tv.vote_average))?'fa-regular':'fa-solid'" :key="n"></i>
                    </li>
                </ul>
            </div>
        </div> -->
    </div>
</template>

<script>

export default {
    name: 'AppMain',
    props: {
        MovieList: Array,
        TvList: Array
    },
    data(){
        return{
            flags:['it', 'en', 'es']
        }
    },
    methods: {
        getVote(decimalVote){
            return Math.ceil(decimalVote / 2);
        }
    }
}
</script>

<style lang="scss">
    .container-main{
        padding: 0 25px;

            .movie{
                display: flex;
                width: calc(100% / 3);
            }
    }
</style>