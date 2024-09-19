<script>
export default {
    name: 'CardComponent',
    props: {
        card: {
            type: Object,
            required: true
        }
    },
    methods: {
        showDetails() {
            alert(`Dettagli della carta: ${this.card.name}`);
        }
    }
}
</script>

<template>
    <div class="col-2 mb-4"> <!-- Mantiene 5 carte per riga -->
        <div class="card-container">
            <div class="card-details text-center">
                <h5 class="card-title">{{ card.name }}</h5>
                <p class="card-type">{{ card.type }}</p>
            </div>
            <div class="card-flip">
                <div class="card-front">
                    <img :src="card.card_images[0].image_url" alt="Card Front" class="card-image" />
                </div>
                <div class="card-back">
                    <img src="https://vignette.wikia.nocookie.net/yugioh/images/9/95/SlifertheSkyDragon-GBI-AE-Back.png/revision/latest/scale-to-width-down/328?cb=2010072608370" alt="Card Back" class="card-image" />
                </div>
            </div>
            <button class="btn btn-primary mt-2" @click="showDetails">Dettagli</button>
        </div>
    </div>
</template>

<style scoped>
.card-container {
    width: 100%;
    height: 100%;
    perspective: 1500px;
    position: relative;
    border: 1px solid #41f3fd;
    border-radius: 10px;
    overflow: hidden;
    background-color: #2c3e50;
    transition: transform 0.3s;
}

.card-flip {
    position: absolute;
    width: 100%;
    height: 100%;
    transform-style: preserve-3d;
    transition: transform 1.2s;
}

.card-container:hover .card-flip {
    transform: rotateY(180deg);
}

.card-front,
.card-back {
    position: absolute;
    width: 100%;
    height: 100%;
    backface-visibility: hidden;
}

.card-image {
    width: 100%;
    height: auto;
    border-radius: 10px;
}

.card-back {
    transform: rotateY(180deg);
}

.card-title {
    color: #ffffff;
    font-size: 1rem;
    font-weight: bold;
}

.card-type {
    font-size: 0.9rem;
    font-weight: bold;
    color: #ecf0f1;
}

.card-details {
    opacity: 1;
    transition: opacity 0.5s ease-in-out;
}
</style>