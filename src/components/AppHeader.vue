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
    font-family: "Arial", sans-serif;
    background-color: #2c3e50;
    color: #ecf0f1;
    padding: 1.5rem;
    box-shadow: 0 4px 10px rgba(0, 0, 0, 0.2);
    text-align: center;
    border-bottom: 2px solid #41f3fd;
}

.logo {
    height: 60px;
    margin-right: 1.5rem;
}

h1 {
    font-size: 2rem;
    margin: 0;
    font-weight: bold;
    text-transform: uppercase;
}
</style>