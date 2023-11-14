<script>

export default {

    //Utilizzo il metodo delle props per trasferire i dati dal componente padre App.vue al componente figlio ProjectCard.vue
    props: {

        project: {
            type: Object,
            required: true
        },

    },

};

</script>


<template>
    <div class="card text-center" style="width: 18rem;">

        <img :src="project.thumb" class="card-img-top" alt="Project Image">

        <div class="card-body">
            <h5 class="card-title">{{ project.title }}</h5>
            <p class="card-text">{{ project.description }}</p>
        </div>

        <ul class="list-group list-group-flush">

            <li class="list-group-item"><span class="badge text-light" :style="`background-color: rgb(${project.type.colour})`">{{ project.type.name }}</span></li>

            <li class="list-group-item"><span class="badge me-1" v-for="technology in project.technologies" :key="technology.id" :style="`background-color: rgb(${technology.colour})`">{{ technology.name }}</span></li>

            <li class="list-group-item">{{ project.published_date }}</li>
            <li class="list-group-item">{{ project.language }}</li>

        </ul>

        <div class="card-body">
            <a href="{{ project.link }}" target="_blank" class="btn btn-primary"><i class="fa-brands fa-github"></i></a>
        </div>

    </div>
</template>



<style lang="scss" scoped>
.card {

    box-shadow: rgb(38, 57, 77) 0px 20px 30px -10px;
    transition: transform 0.3s ease-out;


    &:hover {
        transform: scale(1.1);
    }

}
</style>