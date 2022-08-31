<template>
    <div class="container">
        <div class="title">
            <h1>BOOLFLIX</h1>
        </div>
        <div>
            <input type="text" v-model="inputText" placeholder="Cerca" @keyup.enter="$emit('search',inputText)">
            <button  @click="$emit('search',inputText)">Cerca</button>
        </div>
    </div>
</template>

<script>
export default {
    name: 'AppHeader',
    data(){
        return{
            inputText: '',
        }
    },
}
</script>

<style lang="scss">

.container{

    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 10px 25px;
    background-color: #000;
    height: 70px;

    .title{
        color: rgb(227, 0, 0);
    }
}

</style>