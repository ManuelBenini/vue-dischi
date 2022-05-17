<template>

    <main>
        <div class="container d-flex flex-wrap">
            <CardComp :key="`album${index}`" 
                v-for="(album, index) in albums"
                :albumData="album"
            />
        </div>
    </main>
  
</template>

<script>
    import CardComp from './CardComp.vue';
    import axios from 'axios';

    export default {
        name: "MainComp",
        components: { CardComp },
        data(){
            return{
                apiUrl: 'https://flynn.boolean.careers/exercises/api/array/music',
                albums: [],
                isApiLoaded: false
            }
        },
        methods:{
            getApi(){
                axios.get(this.apiUrl)
                .then(response =>{
                    console.log(response.data);
                    this.albums = response.data.response;
                    this.isApiLoaded = true
                })
                .catch(error =>{
                    console.log(error);
                })
            }
        },
        mounted(){
            this.getApi();
        }

    }
</script>

<style lang="scss" scoped>
    @import '../assets/style/vars';

    main{
        min-height: calc(100vh - 60px);
        background-color: $primary-color;
        padding-top: 50px;
    }

</style>