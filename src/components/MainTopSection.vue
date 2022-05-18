<template>

    <section>
        <img src="../assets/img/logo-small.svg" alt="spotify logo">   
        
        <select name="" id="">
            <option value="">Seleziona un genere</option>
            <option value="">Rock</option>
            <option value="">Pop</option>
            <option value="">Jazz</option>
            <option value="">Metal</option>
        </select>
    </section>
  
</template>

<script>
export default {
    name: 'MainTopSection'
}
</script>

<style lang="scss" scoped>
    @import '../assets/style/vars';

    section{
        height: 60px;
        background-color: $secondary-color;
        display: flex;
        justify-content: space-between;
        align-items: center;
        padding: 0 10px;
        img{
            width: 35px;
            filter: invert(25%) sepia(9%) saturate(3330%) hue-rotate(83deg) brightness(119%) contrast(79%);
        }
        
        select{
            padding: 8px 10px;
        }
    }

</style>