<template>
<div class="container-fluid px-5">
    <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/1/19/Spotify_logo_without_text.svg/2048px-Spotify_logo_without_text.svg.png" alt="">
</div>
</template>

<script>
export default {
name: 'Header',
}
</script>

<style lang="scss" scoped>
div{
    height: 80px;
    background-color: #2e3a46;
    display: flex;
    align-items: center;
    img{
        width: 50px;
    }
}
</style>