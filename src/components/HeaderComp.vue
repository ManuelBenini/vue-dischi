<template>

    <header>
        <div class="logo">
            <img src="../assets/img/logo-small.svg" alt="spotify logo">   
        </div>
        
        <select name="" id="">
            <option value="">Seleziona un genere</option>
            <option value="">Rock</option>
            <option value="">Metal</option>
            <option value="">Opera</option>
        </select>
    </header>
  
</template>

<script>
export default {
    name: 'HeaderComp'
}
</script>

<style lang="scss" scoped>
    @import '../assets/style/vars';

    header{
        height: 60px;
        background-color: lighten($primary-color, 30%);
        display: flex;
        justify-content: space-between;
        align-items: center;
        padding: 0 10px;
        .logo{
            background-color: black;
            width: 40px;
            height: 40px;
            border-radius: 50%;
            img{
                width: 100%;
                filter: invert(25%) sepia(9%) saturate(3330%) hue-rotate(83deg) brightness(119%) contrast(79%);
            }
        }
        
        select{
            padding: 8px 10px;
        }
    }

</style>