<script>
export default {
    name: 'LoaderComponent'
}
</script>

<template>
    <div class="loader-container">
        <div class="loader-bar loader-bar-1"></div>
        <div class="loader-bar loader-bar-2"></div>
        <div class="loader-bar loader-bar-3"></div>
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

.loader-bar {
    width: 10px;
    height: 40px;
    background-color: #41f3fd;
    margin: 4px;
    box-shadow: 0 0 12px 3px #0882ff;
    animation: loader-animation 1.5s ease-in-out infinite;
}

.loader-bar-1 {
    animation-delay: 0s;
}

.loader-bar-2 {
    animation-delay: 0.5s;
}

.loader-bar-3 {
    animation-delay: 1s;
}
</style>