<script>
export default {
    name: 'TotalResults',
    props: {
        total: {
            type: Number,
            required: true
        }
    }
}
</script>

<template>
    <div class="text-end my-4 text-white">
        <h4>Carte totali: {{ total }}</h4>
    </div>
</template>

<style scoped>
</style>