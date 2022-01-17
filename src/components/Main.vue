<template>
<div class="container-fluid bg">
    <div class="container-70">
        <div class="row row-cols-5 pt-5" v-if="songs">
                <Card  v-for="(song, index) in songs" :key="index" 
                    :poster="song.poster"
                    :title="song.title"
                    :author="song.author"
                    :year="song.year"
                />
             </div>
        <div v-else>
            <h1>Loading...</h1>
        </div>
    </div>
</div>
</template>

<script>
import axios from 'axios';
import Card from './Card.vue'
export default {
name: 'Main',
components: {
    Card,
},
data(){
    return{
        queryApi: 'https://flynn.boolean.careers/exercises/api/array/music',
        songs: null,
    };
},
mounted() {
    setTimeout(() => {
        axios.get(this.queryApi)
        .then((result) => {
        console.log(result.data.response);
        this.songs = result.data.response;
        })
        .catch((error) => {
        console.log(error);
        })
    }, 1500)
    
}
}
</script>

<style lang="scss" scoped>
*{
    border: 0;
    margin: 0;
    box-sizing: border-box;
}
.bg{
    background-color: #1e2d3b;
    height: calc(100vh - 80px);
    display: flex;
    align-items: center;
    .container-70{
        width: 70%;
        margin: 0 auto;
        
    }
}
h1{
    color: white;
    text-transform: uppercase;
    text-align: center;
}


</style>