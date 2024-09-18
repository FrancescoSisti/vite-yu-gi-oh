<script>
export default {
    name: 'CardComponent',
    props: {
        card: {
            type: Object,
            required: true
        }
    }
}
</script>

<template>
    <div id="card-component" class="col-6 col-md-4 col-lg-3 mb-4">
        <div class="card-container">
            <div class="card-flip">
                <div class="card-front">
                    <img src="https://vignette.wikia.nocookie.net/yugioh/images/9/95/SlifertheSkyDragon-GBI-AE-Back.png/revision/latest/scale-to-width-down/328?cb=2010072608370"
                        alt="Card Back" />
                </div>
                <div class="card-back">
                    <img :src="card.card_images[0].image_url" :alt="card.name" />
                </div>
            </div>
        </div>
        <div class="card-details text-center mt-2">
            <h5 class="card-title mb-4">{{ card.name }}</h5>
            <p class="card-type">{{ card.type }}</p>
        </div>
    </div>
</template>

<style lang="scss" scoped>
.card-container {
    width: 100%;
    height: 0;
    padding-bottom: 150%;
    perspective: 1500px;
    position: relative;
}

.card-flip {
    position: absolute;
    width: 100%;
    height: 100%;
    transform-style: preserve-3d;
    transition: transform 1.2s;
}

.card-container:hover .card-flip {
    transform: rotateY(540deg);
}

#card-component:hover .card-details {
    opacity: 1;
    transform: translateY(0);
}

.card-front,
.card-back {
    position: absolute;
    width: 100%;
    height: 100%;
    backface-visibility: hidden;
    top: 0;
    left: 0;
}

.card-front img {
    width: 100%;
    height: auto;
}

.card-back {
    transform: rotateY(180deg);

    img {
        width: 100%;
        height: auto;
    }
}

.card-title {
    color: #fff;
    font-size: 1rem;
    font-weight: bold;
}

.card-type {
    font-size: 0.9rem;
    font-weight: bold;
}

.card-title,
.card-type {
    font-family: "Krub", sans-serif;
}

.card-details {
    opacity: 0;
    transition: opacity 0.5s ease-in-out, transform 0.5s ease-in-out;
}
</style>