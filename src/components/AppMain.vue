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
            // Dati per le carte
            cards: [],
            // Flag di caricamento
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
            <div class="row justify-content-center">
                <div class="col-2" v-for="card in cards" :key="card.id">
                    <CardComponent :card="card" />
                </div>
            </div>
        </div>
    </main>
</template>

<style scoped>
header {
    font-family: "Krub", sans-serif;
}

img {
    height: 100px;
}
</style>