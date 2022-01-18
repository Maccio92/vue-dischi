<template>
<div class="container-fluid bg">
    <div>
        <label for="type">Filtra Per Genere </label>
        <select v-model="selectionGenre" name="genre" id="genre" @change="filter">
            <option value="all">All</option>
            <option value="rock">Rock</option>
            <option value="pop">Pop</option>
            <option value="jazz">Jazz</option>
            <option value="metal">Metal</option>
        </select>
    </div>
    <div class="container-70">
        <div class="row row-cols-5 pt-5 gx-3" v-if="filtered">
                <Card  v-for="(song, index) in filtered" :key="index" 
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
        selectionGenre: 'all',
        filtered: null,
    };
},
mounted() {
    setTimeout(() => {
        axios.get(this.queryApi)
        .then((result) => {
        console.log(result.data.response);
        this.songs = result.data.response;
        this.filtered = result.data.response;
        })
        .catch((error) => {
        console.log(error);
        })
    }, 1500)
    
},
methods: {
    filter() {
        this.filtered = this.songs
        if(this.selectionGenre != 'all'){
            this.filtered = this.songs.filter(element => element.genre.toLowerCase()  === this.selectionGenre);
            console.log(this.filtered);
        }
		return this.filtered;
		}
    }
}
</script>

<style lang="scss" >
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