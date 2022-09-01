<template>
    <div class="container-main">

        <div class="movie">
            <h2>FILM</h2>
            <ul class="card">
                <li v-for="(movie, index) in MovieList" :key="index">
                    <div class="flip-card">
                        <div class="flip-card-inner">
                            <div class="flip-card-front">
                                <img :src="'https://image.tmdb.org/t/p/w342' + movie.poster_path " :alt="movie.title">
                            </div>
                            <div class="flip-card-back style-back-card">
                                <div>
                                    Titolo: {{movie.title}}
                                </div>
                                <div>
                                    Titolo originale: {{movie.original_title}}
                                </div>
                                <div>
                                    Lingua: <img v-if="flags.includes(movie.original_language)" :src='"../assets/images/" + movie.original_language + ".png"'>
                                    <span v-else>{{movie.original_language}}</span> 
                                </div>
                                <div>
                                    Voto: <i v-for="n in 5" class="fa-star" :class="(n >= getVote(movie.vote_average))?'fa-regular':'fa-solid'" :key="n"></i>
                                </div>
                                <div>
                                    Owerview: {{movie.overview}}
                                </div>
                            </div>
                        </div>
                    </div>
                </li>
            </ul>
        </div>

        <hr>

   <div class="tv">
            <h2>SERIE TV</h2>               
            <ul class="card">
                <li v-for="(tv, index) in TvList" :key="index">
                    <div class="flip-card">
                        <div class="flip-card-inner">
                            <div class="flip-card-front">
                                <img :src="'https://image.tmdb.org/t/p/w342' + tv.poster_path " :alt="tv.name">
                            </div>
                            <div class="flip-card-back style-back-card">
                                <div>
                                    Titolo: {{tv.name}}
                                </div>
                                <div>
                                    Titolo originale: {{tv.original_name}}
                                </div>
                                <div>
                                    Lingua: <img v-if="flags.includes(tv.original_language)" :src='"../assets/images/" + tv.original_language + ".png"'>
                                    <span v-else>{{tv.original_language}}</span> 
                                </div>
                                <div>
                                    Voto: <i v-for="n in 5" class="fa-star" :class="(n >= getVote(tv.vote_average))?'fa-regular':'fa-solid'" :key="n"></i>
                                </div>
                                <div>
                                    Owerview: {{tv.overview}}
                                </div>
                            </div>
                        </div>
                    </div>
                </li>
            </ul>
        </div>
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

        h2{
            text-align: center;
            color: white;
        }
        
        .card{
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            align-items: flex-end;

            li{
                display: inline;
                list-style: none;
                width: calc(100vw / 6);
                padding: 20px 0px;
            }
        }

        .flip-card {
            background-color: transparent;
            width: 330px;
            height: 500px;
            perspective: 1000px;
            
        }

        .flip-card-inner {
            position: relative;
            width: 100%;
            height: 100%;
            text-align: center;
            transition: transform 0.6s;
            transform-style: preserve-3d;
            box-shadow: 0 4px 8px 0 rgba(0,0,0,0.2);
        }

        .flip-card:hover .flip-card-inner {
            transform: rotateY(180deg);
        }

        .flip-card-front, .flip-card-back {
            position: absolute;
            width: 100%;
            height: 100%;
            -webkit-backface-visibility: hidden;
            backface-visibility: hidden;
        }

        .flip-card-front {
            background-color: #bbb;
            color: black;

            img{
                height: 500px;
                border: solid 1px white;
            }
        }

        .flip-card-back {
            background-color: black;
            color: white;
            transform: rotateY(180deg);
            border: solid 1px white;

            img{
                width: 40px;
            }
        }

        .style-back-card{
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: flex-start;
            padding: 0 15px ;

                div{
                    padding: 10px 0;
                }
        }

    }
</style>