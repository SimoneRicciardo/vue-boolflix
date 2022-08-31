<template>
    <div class="container-main">
        <div>
            <img src="" alt="">
        </div>
        <div class="info-film">    
            <ul>
                <li v-for="(info, index) in MovieList" :key="index">
                    {{info.title}}-
                    {{info.original_title}}-
                    {{info.original_language}}-
                    {{info.vote_average}}-
                </li>
            </ul>
        </div>
    </div>
</template>

<script>

export default {
    name: 'AppMain',
    props: {
        MovieList: Array
    },
    computed: {
        flags(){
            this.MovieList.forEach()
        }
    }
}
</script>

<style lang="scss">
    .container-main{
        padding: 0 25px;
    }
</style>