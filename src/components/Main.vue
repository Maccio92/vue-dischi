<template>
<main class="bg">
    
    <div class="container">
        <div class="row col d-flex justify-content-center">
            <Selection  
            @search="filter($event)"
            />
        </div>
        <div class="row row-cols-5 pt-5 gx-3" v-if="songs">
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

</main>

</template>

<script>
import axios from 'axios';
import Card from './Card.vue';
import Selection from './Selection.vue'

export default {
name: 'Main',
components: {
    Card,
    Selection,
},
data(){
    return{
        queryApi: 'https://flynn.boolean.careers/exercises/api/array/music',
        songs: null,
        // selectionGenre: 'all',
        filtered: null,
    };
},
mounted() {
    setTimeout(() => {
        this.getCards();
    }, 1500)
    
},
methods: {
    getCards () {
			axios.get('https://flynn.boolean.careers/exercises/api/array/music')
			.then((result) => {
				this.songs = result.data.response;
				this.filtered = result.data.response;
				
			})
			.catch((error) => {
				console.log(error);
			})
		},
    filter(text) {
        this.songs = this.filtered;
        if(text != 'all'){
            this.songs = this.songs.filter(element => {
                return element.genre.toLowerCase().includes(text.toLowerCase())
                });
        }
		}
    }
}
</script>

<style lang="scss" >
.bg{
    background-color: #1e2d3b;
    height: calc(100vh - 80px);
}
h1{
    color: white;
    text-transform: uppercase;
    text-align: center;

}
</style>