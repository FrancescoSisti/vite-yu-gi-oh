<script>
export default {
    name: 'ArchetypeFilter',
    props: {
        archetypes: {
            type: Array,
            required: true
        }
    },
    methods: {
        handleChange(event) {
            this.$emit('change', event.target.value); // Emmetti l'archetipo selezionato
        }
    }
}
</script>

<template>
    <div class="mb-4">
        <label for="archetype-select" class="form-label text-white">Filtra per archetipo:</label>
        <select id="archetype-select" class="form-select" @change="handleChange">
            <option value="">Tutti</option>
            <option v-for="archetype in archetypes" :key="archetype.id" :value="archetype.id">
                {{ archetype.name }}
            </option>
        </select>
    </div>
</template>

<style scoped>
/* Stili per il filtro */
</style>