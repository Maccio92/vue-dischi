<template>
<div class="container-fluid bg">
    <div class="container-70">
        <div class="row row-cols-5 pt-5">
            <div class=" col py-4 g-3 flex" v-for="(song, index) in songs" :key="index">
                <img :src="song.poster" alt="">
                <h2>{{song.title}}</h2>
                <h3>{{song.author}}</h3>
                <h4>{{song.year}}</h4>
            </div>
        </div>
    </div>
</div>
</template>

<script>
import axios from 'axios';
export default {
name: 'Main',
data(){
    return{
        queryApi: 'https://flynn.boolean.careers/exercises/api/array/music',
        songs: [],
    };
},
created() {
    axios.get(this.queryApi)
        .then((result) => {
        console.log(result.data.response);
        this.songs = result.data.response;
        })
        .catch((error) => {
        console.log(error);
        })
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
        .flex{
            display: flex;
            flex-direction: column;
            justify-content: start;
            align-items: center;
        }
        .col{
            background-color: #2e3a46;
            img{
            width: 100%;
            }
        }
    }
}
h2{
    font-size: 1.2em;
    color: white;
    text-align: center;
    text-transform: uppercase;
    margin-bottom: 0.5em;
}
h3, h4{
    color: #808080;
     text-align: center;
     font-size: 0.7em;
     
}

</style>