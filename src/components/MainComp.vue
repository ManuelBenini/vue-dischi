<template>

    <main>
        <MainTopSection />

        <section class="main-section">

            <div class="container d-flex flex-wrap" v-if="isApiLoaded">
                <CardComp :key="`album${index}`" 
                    v-for="(album, index) in albums"
                    :albumData="album"
                />
            </div>
    
            <div class="container d-flex flex-wrap" v-else>
                <LoaderComp loadingMessage=" 'Il rock non eliminerà i tuoi problemi. Ma ti permetterà di ballarci sopra.' " />
            </div>
        </section>

    </main>
  
</template>

<script>
    import CardComp from './CardComp.vue';
    import axios from 'axios';
import LoaderComp from './LoaderComp.vue';
import MainTopSection from './MainTopSection.vue';

    export default {
        name: "MainComp",
        components: { CardComp, LoaderComp, MainTopSection },
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
        min-height: 100vh;
        background-color: $primary-color;
        .main-section{
            padding-top: 60px;
        }
    }

</style>