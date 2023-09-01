
<script>

import axios from 'axios';

export default {
    data() {
        return {
            searchQuery: '',
            results: [],
            showInput: false,
            tvResults: []
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
                // this.results = response.data.results;
                this.movieResults = response.data.results.filter(result => result.media_type === "movie");
                this.tvResults = response.data.results.filter(result => result.media_type === "tv");
            }).catch(error => {
                console.error(error);
            });
        }
    }
}
</script>
<!-- <img src="../assets/img/film-radiobussola.jpg" alt=""> -->

<template>
    <nav class="navbar navbar-expand-lg bg-transparent">
        <div class="container-mio d-flex justify-content-between align-items-center">

            <div class="d-flex align-items-center">
                <img class="bg-transparent logo-iniziale  bg-dark"
                    src="../assets/img/png-clipart-logo-netflix-nasdaq-nflx-brand-television-copywriter-floor-television-text.png"
                    alt="">
                <ul class="navbar-nav d-flex text-white">
                    <li class="nav-item "><a href="#" class="nav-link ">Home</a></li>
                    <li class="nav-item"><a class="nav-link " href="#">Serie TV</a></li>
                    <li class="nav-item"><a class="nav-link" href="#">Film</a></li>
                    <li class="nav-item"><a class="nav-link" href="#">Nuovi popolari</a></li>
                    <li class="nav-item"><a class="nav-link" href="#">La mia lista</a></li>
                    <li class="nav-item"><a class="nav-link" href="#">Sfoglia per lingua</a></li>
                </ul>
            </div>

            <div class="d-flex align-items-center">
                <input type="text" v-model="searchQuery" placeholder="Cerca film o serie TV" class="input-mio" ><!--v-show="showInput"-->
                <button @click="fetchData" class="animazione">Cerca</button>
                <i class="fa-regular fa-bell"></i>
                <img src="../assets/img/png-transparent-netflix-macos-bigsur-icon.png" class="logo-iniziale" alt="">
            </div>
        </div>



    </nav>

        <div  class="container-mio bg p-4 slider">
            
            <div  class="d-flex flex-wrap">
                <div class="card sfondo border border-0 " style="width: 18rem;" v-for="result in results" :key="result.id">
                    <img class="card-in-hover card-img-top carte card-img-top img-prova" :src="'https://image.tmdb.org/t/p/w200' + result.poster_path"
                            alt="Poster">
                    <div class="card-body card-prova">
                        <h5 class="card-title">Titolo {{ result.title || result.name }}</h5>
                        <p class="card-text">Titolo Originale {{ result.original_title || result.original_name }}</p>
                        <p>Lingua {{ result.original_language }}</p>
                        <p>Voto {{ result.vote_average }}</p>
                    </div>
                </div>
            </div>
        </div>

        <div class="divisore"></div><!--non va cosi-->

        <div  class="container-mio bg p-4 slider">
            <div  class="d-flex flex-wrap">
                <div class="card sfondo border border-0 " style="width: 18rem;" v-for="result in tvResults" :key="result.id">
                    <img class="card-in-hover card-img-top carte card-img-top img-prova" :src="'https://image.tmdb.org/t/p/w200' + result.poster_path"
                            alt="Poster">
                    <div class="card-body card-prova">
                        <h5 class="card-title">Titolo serie {{ result.title || result.name }}</h5>
                        <p class="card-text">Titolo Originale {{ result.original_title || result.original_name }}</p>
                        <p>Lingua {{ result.original_language }}</p>
                        <p>Voto {{ result.vote_average }}</p>
                    </div>
                </div>
            </div>
        </div>


    <!-- <div class="container-mio bg p-4">
        <div class="d-flex flex-wrap">
            <div class="card sfondo p-2 " v-for="result in results" :key="result.id">
                <img class="card-in-hover card-img-top carte card-img-top img-prova" :src="'https://image.tmdb.org/t/p/w200' + result.poster_path"
                    alt="Poster">
                <div class="card-body type">
                    <h5 class="card-title text-white">Titolo {{ result.title || result.name }}</h5>
                    <p class="card-text">Titolo Originale {{ result.original_title || result.original_name }}</p>
                    <p>Lingua {{ result.original_language }}</p>
                    <p>Voto {{ result.vote_average }}</p>
                </div>
            </div>
        </div>
    </div> -->

    <!-- <div class="ratio ratio-16x9">
        <iframe src="https://www.youtube.com/embed/zpOULjyy-n8?rel=0" title="YouTube video" allowfullscreen></iframe>
    </div> -->
</template>


<style lang="scss" scoped>
.logo-iniziale {
    width: 100px;
}

.sfondo {
    padding: 5px;
}
.container-mio {
    width: 100%;

}

// .card-in-hover:hover {
//     width: 400px;
//     transition: 2s;
// }

// .carte {
//     width: 200px;
// }

img {
    width: 100%;
}
// nav {
//     position: absolute;
// }


a:hover {
    color: rgb(100, 99, 99);
}

a {
    color: white;
    font-size: 14px;
    cursor: pointer;

}

.divisore {
    width: 100%;
    height: 200px;
    background-color: red;
}


i {
    color: white;
}

.img-prova:hover + .card-prova {
    display: block;
    width: 300px;
    
    // position: absolute;  //per far mettere le cose sopra la foto 
}

.card-prova:hover {
    display: block;
}

.img-prova {
    transition: 2s;
}
.card-prova {
    display: none;
}


</style>


<!--<div class="row g-0 bg-body-secondary position-relative">
  <div class="col-md-6 mb-md-0 p-md-4">
    <img src="..." class="w-100" alt="...">
  </div>
  <div class="col-md-6 p-4 ps-md-0">
    <h5 class="mt-0">Columns with stretched link</h5>
    <p>Another instance of placeholder content for this other custom component. It is intended to mimic what some real-world content would look like, and we're using it here to give the component a bit of body and size.</p>
    <a href="#" class="stretched-link">Go somewhere</a>
  </div>
</div>--><!--per le icone dei i film-->