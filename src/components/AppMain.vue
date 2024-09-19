<script>
import axios from 'axios';
import CardComponent from './CardComponent.vue'
import LoaderComponent from './LoaderComponent.vue'

export default {
    name: 'AppMain',
    components: {
        CardComponent,
        LoaderComponent
    },
    data() {
        return {
            cards: [],
            loading: true
        };
    },
    mounted() {
        this.fetchCards();
    },
    methods: {
        fetchCards() {
            const minLoadingTime = 1000;
            const startTime = Date.now();

            axios
                .get('https://db.ygoprodeck.com/api/v7/cardinfo.php?num=20&offset=0')
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
        }
    }
}
</script>

<template>
    <main class="container mt-4">
        <div v-if="loading">
            <LoaderComponent />
        </div>
        <div v-else>
            <div class="text-end my-4 text-white">
                <h4>Carte totali: {{ cards.length }}</h4>
            </div>
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