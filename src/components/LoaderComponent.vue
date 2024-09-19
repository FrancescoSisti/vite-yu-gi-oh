<script>
export default {
    name: 'LoaderComponent'
}
</script>

<template>
    <div class="loader-container">
        <div class="loader-circle"></div>
        <p class="loading-text">Caricamento in corso...</p>
    </div>
</template>

<style scoped>
.loader-container {
    height: 80vh;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    padding: 10px;
    background-color: rgba(0, 0, 0, 0.7); /* Sfondo scuro per contrasto */
    border-radius: 10px; /* Angoli arrotondati */
}

.loading-text {
    margin-top: 10px;
    color: #ffffff; /* Colore del testo bianco */
    font-size: 1.5rem; /* Dimensione del testo aumentata */
}

.loader-circle {
    width: 60px; /* Cerchio più grande */
    height: 60px;
    border: 6px solid #41f3fd;
    border-top: 6px solid transparent;
    border-radius: 50%;
    animation: spin 1s linear infinite;
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
