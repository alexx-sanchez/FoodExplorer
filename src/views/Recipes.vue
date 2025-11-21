<script setup>
import { ref } from 'vue';
import { RouterLink, RouterView } from 'vue-router';

const receptes = ref([
    {
        id: 1,
        nom: 'Pizza Margarita',
        descripcio: 'Pizza italiana clàssica amb tomàquet, mozzarella i alfàbrega.',
        foto: "https://www.annarecetasfaciles.com/files/pizza-margarita-1-scaled.jpg"
    },
    {
        id: 2,
        nom: 'Amanida César',
        descripcio: 'Amanida clàssica amb enciam, crostons, parmesà i salsa César.',
        foto: "https://gourmet.iprospect.cl/wp-content/uploads/2016/09/EnsaladaCesar2.webp"
    },
    {
        id: 3,
        nom: 'Brownie de xocolata',
        descripcio: 'Brownie americà esponjós i intens de xocolata.',
        foto: "https://hips.hearstapps.com/hmg-prod/images/brownie-chocolate-helado-elle-gourmet-64d48f5ba8668.jpg?crop=0.9655555555555556xw:1xh;center,top&resize=1200:*"
    }
]);
</script>

<template>
    <h1>Les nostres receptes</h1>

    <div class="container">
        <section v-for="recepta in receptes" :key="recepta.id">
            <img :src="recepta.foto" :alt="recepta.nom" />
            <h3>{{ recepta.nom }}</h3>
            <p>{{ recepta.descripcio }}</p>
            <RouterLink :to="`/receptes/${recepta.id}`">Veure detall</RouterLink>
        </section>
    </div>
    </template>

<style scoped>
.container {
    display: flex;
    gap: 1rem;
}

section {
    width: 250px;
    text-align: center;
    border: 1px solid #ddd;
    border-radius: 8px;
    padding: 1rem;
    box-shadow: 0 2px 6px rgba(0, 0, 0, 0.1);
}

img {
    width: 100%;
    height: 200px;
    object-fit: cover;
}
</style>
