<template>

    <main>
        <MainTopSection @changeGenre="selectedGenre" @changeArtist="selectedArtist" :albumGenres="albumsGenres" :albumArtists="albumsArtists" />

        <section class="main-section">

            <div class="container d-flex flex-wrap" v-if="isApiLoaded">
                <CardComp :key="`album${index}`" 
                    v-for="(album, index) in albumArrayWithMultipleFilters"
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
                albumsGenres: [],
                albumsArtists: [],
                isApiLoaded: false,
                albumSelectByGenre: '',
                albumSelectByArtist: ''
            }
        },
        methods:{
            getApi(){
                axios.get(this.apiUrl)
                .then(response =>{
                    console.log(response.data);
                    this.albums = response.data.response;
                    this.isApiLoaded = true;
                    this.genreArtistPush();
                })
                .catch(error =>{
                    console.log(error);
                })
            },
            selectedGenre(string){
                this.albumSelectByGenre = string
            },
            selectedArtist(string){
                this.albumSelectByArtist = string
            },
            genreArtistPush(){
                this.albums.forEach(album => {
                    if(!this.albumsGenres.includes(album.genre)){
                        this.albumsGenres.push(album.genre)
                    }
                    if(!this.albumsArtists.includes(album.author)){
                        this.albumsArtists.push(album.author)
                    }
                });
                console.log('array generi',this.albumsGenres);
                console.log('array artisti',this.albumsArtists);
            }

        },
        computed:{
            filteredAlbumsByGenre(){
                let albumsByGenre = [];
                if(this.albumSelectByGenre === 'none'){
                    albumsByGenre = this.albums;
                }else{
                    albumsByGenre = this.albums.filter(album =>{
                        return album.genre.toLowerCase().includes(this.albumSelectByGenre.toLowerCase());
                    })
                }
                console.log('array filtro genere', albumsByGenre);
                return albumsByGenre;
            },
            albumArrayWithMultipleFilters(){
                let albumsWithFilters = this.filteredAlbumsByGenre;
                if(this.albumSelectByArtist != 'none'){
                    albumsWithFilters = this.filteredAlbumsByGenre.filter(album =>{
                        return album.author.toLowerCase().includes(this.albumSelectByArtist.toLowerCase());
                    })
                }
                console.log('array con filtro genere + artista', albumsWithFilters);
                return albumsWithFilters;
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