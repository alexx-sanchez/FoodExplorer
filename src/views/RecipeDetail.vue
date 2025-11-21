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
        ],
        foto: "https://www.annarecetasfaciles.com/files/pizza-margarita-1-scaled.jpg"
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
        ],
        foto: "https://gourmet.iprospect.cl/wp-content/uploads/2016/09/EnsaladaCesar2.webp"
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
        ],
        foto: "https://hips.hearstapps.com/hmg-prod/images/brownie-chocolate-helado-elle-gourmet-64d48f5ba8668.jpg?crop=0.9655555555555556xw:1xh;center,top&resize=1200:*"
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
    <div class="container">
        <img :src="recepta.foto" :alt="recepta.nom">
        <div class="info-container">
            <h2>{{ recepta.descripcio }}</h2>
            <p>Ingredients</p>
            <ul>
                <li v-for="pas in recepta.ingredients" :key="recepta.id">
                    {{ pas }}
                </li>
            </ul>
            
            <p>Passos a fer</p>
            <ul>
                <li v-for="pas in recepta.passos" :key="recepta.id">
                    {{ pas }}
                </li>
            </ul>

            
        </div>

    </div>
</template>


<style scoped>
/* Contenedor principal */
.container {
    display: flex;
    flex-direction: row;
    align-items: flex-start;
    justify-content: center;
    max-width: 1000px;
    margin: 0 auto;
    padding: 2.5rem;
    gap: 2rem;
    flex-wrap: wrap;
    background: linear-gradient(135deg, #fdfbfb 0%, #ebedee 100%);
    border-radius: 20px;
    box-shadow: 0 12px 30px rgba(0,0,0,0.12);
    transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.container:hover {
    box-shadow: 0 16px 40px rgba(0,0,0,0.18);
}

/* Imagen de la receta */
.container img {
    width: 100%;
    max-width: 420px;
    height: auto;
    border-radius: 20px;
    object-fit: cover;
    box-shadow: 0 6px 18px rgba(0,0,0,0.2);
    transition: transform 0.4s ease, filter 0.4s ease;
}

.container img:hover {
    transform: scale(1.05) rotate(-1deg);
    filter: brightness(1.05);
}

/* Contenedor de la info */
.info-container {
    flex: 1;
    text-align: left;
    display: flex;
    flex-direction: column;
    justify-content: center;
    gap: 1.2rem;
}

/* Títulos */
h1 {
    text-align: center;
    font-size: 3rem;
    font-weight: 800;
    margin-bottom: 2rem;
    color: #1e293b;
    letter-spacing: 1px;
    text-shadow: 2px 2px 6px rgba(0,0,0,0.1);
}

h2 {
    font-size: 1.8rem;
    font-weight: 600;
    margin-bottom: 0.5rem;
    color: #0f172a;
}

/* Listas de ingredientes y pasos */
ul {
    list-style: none;
    padding: 0;
    margin: 0.5rem 0 1rem 0;
    display: flex;
    flex-direction: column;
    gap: 0.6rem;
}

li {
    background: #ffffff;
    margin: 0;
    padding: 0.7rem 1.2rem;
    border-radius: 10px;
    border-left: 5px solid #3b82f6;
    font-size: 1rem;
    font-weight: 500;
    color: #374151;
    box-shadow: 0 3px 8px rgba(0,0,0,0.08);
    transition: transform 0.2s ease, background 0.2s ease;
}

li:hover {
    transform: translateX(5px);
    background: #f0f9ff;
}

/* Resaltar subtítulos */
p {
    font-weight: 700;
    margin-top: 1rem;
    color: #3b82f6;
    font-size: 1.1rem;
    text-transform: uppercase;
    letter-spacing: 0.5px;
}

/* Responsive */
@media (max-width: 768px) {
    .container {
        flex-direction: column;
        align-items: center;
        padding: 1.5rem;
    }

    .info-container {
        text-align: center;
    }

    .container img {
        max-width: 100%;
    }

    h1 {
        font-size: 2.2rem;
    }
}
</style>
