<script>
import axios from 'axios';
import CardComponent from './CardComponent.vue'
import LoaderComponent from './LoaderComponent.vue'
import ArchetypeFilter from './ArchetypeFilter.vue'; // Importa il nuovo componente
import TotalResults from './TotalResults.vue'; // Importa il nuovo componente

export default {
    name: 'AppMain',
    components: {
        CardComponent,
        LoaderComponent,
        ArchetypeFilter,
        TotalResults // Aggiungi il componente qui
    },
    data() {
        return {
            cards: [],
            loading: true,
            archetypes: [], // Aggiungi un array per gli archetipi
            selectedArchetype: null // Aggiungi una variabile per l'archetipo selezionato
        };
    },
    mounted() {
        this.fetchArchetypes(); // Carica gli archetipi all'avvio
        this.fetchCards(); // Carica le carte
    },
    methods: {
        fetchArchetypes() {
            axios.get('https://db.ygoprodeck.com/api/v7/archetypes.php')
                .then((response) => {
                    this.archetypes = response.data.data; // Popola gli archetipi
                });
        },
        fetchCards() {
            const minLoadingTime = 1000;
            const startTime = Date.now();
            const url = this.selectedArchetype 
                ? `https://db.ygoprodeck.com/api/v7/cardinfo.php?archetype=${this.selectedArchetype}` 
                : 'https://db.ygoprodeck.com/api/v7/cardinfo.php?num=20&offset=0';

            axios.get(url)
                .then((response) => {
                    this.cards = response.data.data;
                })
                .finally(() => {
                    const elapsedTime = Date.now() - startTime;
                    const remainingTime = minLoadingTime - elapsedTime;

                    if (remainingTime > 0) {
                        setTimeout(() => {
                            this.loading = false;
                        }, remainingTime);
                    } else {
                        this.loading = false;
                    }
                });
        },
        onArchetypeChange(archetype) {
            this.selectedArchetype = archetype; // Aggiorna l'archetipo selezionato
            this.fetchCards(); // Ricarica le carte in base all'archetipo selezionato
        }
    }
}
</script>

<template>
    <main class="container mt-4">
        <ArchetypeFilter :archetypes="archetypes" @change="onArchetypeChange" /> <!-- Aggiungi il filtro qui -->
        <div v-if="loading">
            <LoaderComponent />
        </div>
        <div v-else>
            <TotalResults :total="cards.length" /> <!-- Aggiungi il componente per i risultati totali -->
            <div class="row">
                <CardComponent v-for="card in cards" :key="card.id" :card="card" />
            </div>
        </div>
    </main>
</template>

<style scoped>
.container {
    background-color: #34495e;
    border-radius: 10px;
    padding: 20px;
}

.row {
    display: flex;
    flex-wrap: wrap; /* Permette di andare a capo */
}

.col-2 {
    flex: 0 0 20%; /* Mantiene 5 carte per riga */
    max-width: 20%; /* Mantiene 5 carte per riga */
}

img {
    height: 100px;
}
</style>