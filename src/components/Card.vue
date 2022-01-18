<template>
<div class="col py-4"> 
    <div class="col-bg">        
        <img class="img-fluid" :src="poster" alt="">
        <h2>{{title}}</h2>
        <h3>{{author}}</h3>
        <h4>{{year}}</h4>
    </div>
</div>
</template>

<script>
export default {
    name: 'Card',
    props: ['poster', 'title', 'author', 'year'],
}
</script>

<style lang="scss" scoped>
.col-bg{
    background-color: #2e3a46;
    height: 100%;
}
h2{
    font-size: 90%;
    color: white;
    text-align: center;
    text-transform: uppercase;
    margin: 0.5em 0; 
}
h3, h4{
    color: #808080;
    text-align: center;
    font-size: 60%;
}
</style>