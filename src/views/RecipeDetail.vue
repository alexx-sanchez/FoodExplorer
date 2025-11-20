<script setup>
import { ref, watch } from 'vue'
import { useRoute } from 'vue-router'

const receptes = ref([
    {
        id: 1,
        nom: 'Pizza Margarita',
        descripcio: 'Pizza italiana clàssica amb tomàquet, mozzarella i alfàbrega.',
        ingredients: [
            'Massa de pizza',
            'Salsa de tomàquet',
            'Formatge mozzarella',
            'Fulles d’alfàbrega',
            'Oli d’oliva',
            'Sal'
        ],
        passos: [
            'Estira la massa de pizza sobre una safata.',
            'Afegeix salsa de tomàquet a la base.',
            'Distribueix la mozzarella uniformement.',
            'Afegeix fulles d’alfàbrega.',
            'Enforna a 220ºC durant 12-15 minuts.',
            'Amaneix amb oli d’oliva i serveix.'
        ]
    },
    {
        id: 2,
        nom: 'Amanida César',
        descripcio: 'Amanida clàssica amb enciam, crostons, parmesà i salsa César.',
        ingredients: [
            'Enciam romà',
            'Crostons de pa',
            'Formatge parmesà',
            'Pit de pollastre (opcional)',
            'Salsa César'
        ],
        passos: [
            'Renta i talla l’enciam.',
            'Cuina el pollastre si vols afegir-lo.',
            'Barreja l’enciam amb la salsa César.',
            'Afegeix crostons i parmesà per sobre.',
            'Serveix fred.'
        ]
    },
    {
        id: 3,
        nom: 'Brownie de xocolata',
        descripcio: 'Brownie americà esponjós i intens de xocolata.',
        ingredients: [
            'Xocolata negra',
            'Mantega',
            'Sucre',
            'Ous',
            'Farina',
            'Nous (opcional)'
        ],
        passos: [
            'Fon la xocolata amb la mantega.',
            'Afegeix el sucre i remena.',
            'Incorpora els ous un a un.',
            'Afegeix la farina i barreja suaument.',
            'Afegeix nous si vols.',
            'Enforna a 180ºC durant 20-25 minuts.'
        ]
    }
]);

const route = useRoute()
const recepta = ref(null)
  
/* Funcio per carregar recepta */
const carregarRecepta = (id) => {
    const newID = parseInt(id)
    recepta.value = receptes.value.find(f => f.id === newID) || null
}

carregarRecepta(route.params.id)

watch(
    () => route.params.id,
    (newID) => carregarRecepta(newID)
)
</script>

<template>
    <h1>{{ recepta.nom }}</h1>
    <h2>{{ recepta.descripcio }}</h2>
</template>