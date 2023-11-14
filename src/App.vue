<script>

import axios from 'axios';
import ProjectCards from './components/ProjectCards.vue';


export default {

  components: {
    ProjectCards
  },

  data() {

    return {

      projectsList: [],
      pagination: {}

    };

  },

  methods: {

    fetchData() {

      const apiProjects = 'http://127.0.0.1:8000/api/projects';

      // Attraverso axios comunico con l'API per ricevere i dati su Vue.js 
      axios.get(apiProjects).then((response) => {

        // console.log(response); 

        // Salvo i dati all'interno dell'array projects 
        this.projectsList = response.data.results.data;

        // Salvo i dati relativi alla pagination
        delete response.data.results.data;
        this.pagination = response.data.results;

      })



    }

  },

  mounted() {

    this.fetchData()

  }

};

</script>


<template>
  <header></header>

  <main>

    <div class="container my-5">

      <div class="row row-cols-3 gap-5">

        <!-- Quando voglio utilizzare il componente ProjectCards devo passare questa lista collegando le props con il data() -->
        <!-- Devo mettere "project" e non "projectsList" altrimenti gli ripasso la lista -->
        <ProjectCards v-for="project in projectsList" :project="project"></ProjectCards>

      </div>

    </div>

  </main>

  <footer></footer>
</template>


<style lang="scss"></style>




