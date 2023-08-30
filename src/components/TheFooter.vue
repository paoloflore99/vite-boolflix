
<script>

import axios from 'axios';

export default {
    data() {
        return {
            searchQuery: '',
            results: []
        };
    },
    methods: {
        fetchData() {
            axios.get("https://api.themoviedb.org/3/search/multi", {
                params: {
                    api_key: "6f8cd03ff26e98213b7ba4fa3b12df8e",
                    query: this.searchQuery
                }
            }).then(response => {
                this.results = response.data.results;
            }).catch(error => {
                console.error(error);
            });
        }
    }
}
</script>
<!-- <img src="../assets/img/film-radiobussola.jpg" alt=""> -->

<template>
    <nav class="navbar navbar-expand-lg ">
        <div class="container-mio d-flex justify-content-between align-items-center">

            <div class="d-flex align-items-center">
                <img class="bg-transparent logo-iniziale"
                    src="../assets/img/png-clipart-logo-netflix-nasdaq-nflx-brand-television-copywriter-floor-television-text.png"
                    alt="">
                <ul class="navbar-nav d-flex">
                    <li class="nav-item">Home</li>
                    <li class="nav-item"><a class="nav-link" href="#">Serie TV</a></li>
                    <li class="nav-item"><a class="nav-link" href="#">Film</a></li>
                    <li class="nav-item"><a class="nav-link" href="#">Nuovi popolari</a></li>
                    <li class="nav-item"><a class="nav-link" href="#">La mia lista</a></li>
                    <li class="nav-item"><a class="nav-link" href="#">Sfoglia per lingua</a></li>
                </ul>
            </div>

            <div class="d-flex align-items-center">
                <input type="text" v-model="searchQuery" placeholder="Cerca film o serie TV">
                <button @click="fetchData">Cerca</button>
                <i class="fa-regular fa-bell"></i>
                <img src="../assets/img/png-transparent-netflix-macos-bigsur-icon.png" class="logo-iniziale" alt="">
            </div>
        </div>
    </nav>




    <div class="container-mio bg p-4">
        <div class="d-flex flex-wrap">
            <div class="card sfondo p-2" v-for="result in results" :key="result.id">
                <img class="card-img-top carte" :src="'https://image.tmdb.org/t/p/w200' + result.poster_path" alt="Poster">
                <div class="card-body type">
                    <h5 class="card-title text-white">Titolo {{ result.title || result.name }}</h5>
                    <p class="card-text">Titolo Originale {{ result.original_title || result.original_name }}</p>
                    <p>Lingua {{ result.original_language }}</p>
                    <p>Voto {{ result.vote_average }}</p>
                </div>
            </div>
        </div>
    </div>
</template>


<style lang="scss" scoped>
.logo-iniziale {
    width: 200px;
}

.container-mio {
    width: 100%;
}

.carte {
    width: 200px;
}
</style>
