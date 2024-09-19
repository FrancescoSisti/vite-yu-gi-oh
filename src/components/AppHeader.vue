<script>
export default {
    name: 'AppHeader'
}
</script>

<template>
    <header class="header bg-dark text-white py-3 shadow-sm">
        <div class="container d-flex align-items-center justify-content-center">
            <img src="../assets/logo.jpeg" alt="Logo" class="logo me-3">
            <h1 class="h5 mb-0">Yu-Gi-Oh Deck</h1>
        </div>
    </header>
</template>

<style scoped>
header {
    font-family: "Open Sans", sans-serif;
    background-color: #343a40;
    color: #fff;
    padding: 1rem;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
}

.logo {
    height: 50px;
    margin-right: 1rem;
}

h1 {
    font-size: 1.5rem;
    margin: 0;
}
</style>