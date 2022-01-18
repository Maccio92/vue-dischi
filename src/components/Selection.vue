<template>
<div class="d-flex justify-content-center mt-3">
        <label for="type">Filtra Per Genere </label>
        <select v-model="selectionGenre" name="genre" id="genre" @change="$emit('search', selectionGenre)">
            <option value="all">All</option>
            <option value="rock">Rock</option>
            <option value="pop">Pop</option>
            <option value="jazz">Jazz</option>
            <option value="metal">Metal</option>
        </select>
    </div>
</template>

<script>
export default {
    name: 'Selection',
    data(){
        return {
            selectionGenre: 'all',
        }
    }

}
</script>

<style>
label{
    color: white;
    margin-right: 1em;
}
</style>