<script>
import TheFooter from './components/TheFooter.vue'
import TheHeader from './components/TheHeader.vue'

export default {
  components : {

    TheFooter,
    TheHeader,


  }
};
</script>

<template>

<body class="bg-black">
 <TheFooter></TheFooter>
<TheHeader></TheHeader>
</body>
</template>

<style lang="scss" scoped>


</style>
<!-- il mio api -->
<!--   6f8cd03ff26e98213b7ba4fa3b12df8e    -->


<!-- api per la ricera dei film -->
<!-- https://api.themoviedb.org/3/search/movie?api_key=6f8cd03ff26e98213b7ba4fa3b12df8e  -->
<!-- https://api.themoviedb.org/3/search/movie?api_key=6f8cd03ff26e98213b7ba4fa3b12df8e&query=quiVaIlNomeDaRicercare -->