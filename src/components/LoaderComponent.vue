<script>
export default {
    name: 'LoaderComponent',
    data() {
        return {
            loadingMessage: 'Caricamento, attendere...',
            isLoading: true
        };
    },
    mounted() {
        // Simula un caricamento di 3 secondi
        setTimeout(() => {
            this.isLoading = false;
        }, 3000);
    }
}
</script>

<template>
    <div v-if="isLoading" class="loader-container">
        <div class="loader-circle"></div>
        <p class="loading-text">{{ loadingMessage }}</p>
    </div>
    <div v-else class="loaded-content">
        <p>Contenuto caricato con successo!</p>
    </div>
</template>

<style scoped>
.loader-container {
    height: 100vh;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    padding: 20px;
    background-color: rgba(0, 0, 0, 0.9); /* Sfondo più scuro per contrasto */
    border-radius: 15px; /* Angoli arrotondati più accentuati */
}

.loading-text {
    margin-top: 15px;
    color: #ffffff; /* Colore del testo bianco */
    font-size: 2rem; /* Dimensione del testo aumentata */
    font-weight: bold; /* Testo in grassetto */
}

.loader-circle {
    width: 80px; /* Cerchio più grande */
    height: 80px;
    border: 8px solid #41f3fd;
    border-top: 8px solid transparent;
    border-radius: 50%;
    animation: spin 1.5s linear infinite; /* Animazione più lenta */
}

@keyframes spin {
    0% {
        transform: rotate(0deg);
    }
    100% {
        transform: rotate(360deg);
    }
}
</style>
