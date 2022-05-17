<template>

    <div class="mb-card">
        <div class="thumb">
            <img :src="albumData.poster">
        </div>

        <h6 class="my-3">{{albumData.title.toUpperCase()}}</h6>
        <p>{{albumData.author}}</p>
        <p>{{albumData.year}}</p>
    </div>
  
</template>

<script>
export default {
    name: 'CardComp',
    props:{
        albumData: Object
    }
}
</script>

<style lang="scss" scoped>
    @import '../assets/style/vars';

    .mb-card{
        text-align: center;
        width: calc(100% / 5 - 30px);
        background-color: $secondary-color;
        padding: 15px;
        margin-right: 30px;
        margin-bottom: 30px;
        img{
            width: 100%;
        }
        h6{
            color: white;
        }
        p{
            margin: 0;
            color: grey;
        }
    }
</style>