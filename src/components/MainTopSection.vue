<template>

    <section>
        <div class="logo">
            <img src="../assets/img/logo-small.svg" alt="spotify logo">   
        </div>
        
        <select 
            name="genre-select" 
            v-model="selectedGenre" 
            @change="$emit('changeGenre', selectedGenre)">
            <option value="none">Seleziona un genere</option>
            <option 
                v-for="(genre, index) in albumGenres" 
                :key="`genre${index}`" 
                :value="genre">
                {{genre}}
            </option>
        </select>

        <select 
            class="mx-3" 
            name="artist-select" 
            v-model="selectedArtist" 
            @change="$emit('changeArtist', selectedArtist)">
            <option value="none">Seleziona un'artista</option>
            <option 
                v-for="(artist, index) in albumArtists" 
                :key="`artist${index}`" 
                :value="artist">
                {{artist}}
            </option>
        </select>
    </section>
  
</template>

<script>
export default {
    name: 'MainTopSection',
    props:{
        albumGenres: Array,
        albumArtists: Array
    },
    data(){
        return{
            selectedGenre: 'none',
            selectedArtist: 'none'
        }
    }
}
</script>

<style lang="scss" scoped>
    @import '../assets/style/vars';

    section{
        height: 60px;
        background-color: $secondary-color;
        display: flex;
        align-items: center;
        padding: 0 10px;
        .logo{
            flex-grow: 1;
            img{
                width: 35px;
                filter: invert(25%) sepia(9%) saturate(3330%) hue-rotate(83deg) brightness(119%) contrast(79%);
            }
        }
        
        
        select{
            padding: 8px 10px;
        }
    }

</style>