<template>
<div class="col py-4 g-3 flex">         
    <img :src="poster" alt="">
    <h2>{{title}}</h2>
    <h3>{{author}}</h3>
    <h4>{{year}}</h4>
</div>
</template>

<script>
export default {
    name: 'Card',
    props: ['poster', 'title', 'author', 'year'],
}
</script>

<style lang="scss" scoped>
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