<script>
export default {
    name: 'LoaderComponent'
}
</script>

<template>
    <div class="loader-container">
        <div class="loader-circle"></div>
    </div>
</template>

<style scoped>
.loader-container {
    height: 80vh;
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 10px;
}

.loader-circle {
    width: 50px;
    height: 50px;
    border: 5px solid #41f3fd;
    border-top: 5px solid transparent;
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
