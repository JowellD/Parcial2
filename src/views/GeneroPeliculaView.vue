<template>
    <div class="container">
      <div class="row d-flex justify-content-center">
        <div class="col-md-4" >
          <!-- <router-link> -->
            <div class="card" v-for="pelicula in page.results" :key="pelicula.id">
              <img :src="'https://image.tmdb.org/t/p/w500' + pelicula.backdrop_path" class="card-img-top" :alt="pelicula.title" />
              <div class="card-body">
                <h5 class="card-title">{{ pelicula.title }}</h5>
                <p class="card-text">{{ pelicula.release_date}}</p>
              </div>
            </div>
          <!-- </router-link> -->
        </div>
      </div>
    </div>
  </template>
  
  <script>
import PeliService from '@/service/PeliService'
  
  export default {
    name: 'GeneroPeliculaView',
    data() {
      return {
        page: {
          results: [],
        },
      };
    },
    async created() {
      const peliculaId = this.$route.params.id;
      this.page = await PeliService.getGeneroPelicula(peliculaId);
      console.log(this.page);
    },
  };
  </script>
  
