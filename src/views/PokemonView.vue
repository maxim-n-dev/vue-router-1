<script setup>
    import { ref, onMounted } from 'vue'

    const pokemons = ref([]);


    onMounted(() => {
        fetchPokemons();
    });

    const fetchPokemons = async () => {
        try {
            const res = await fetch('https://pokeapi.co/api/v2/pokemon?limit=200');
            pokemons.value = await res.json();
            console.log(JSON.stringify(pokemons.value.results))
        } catch (error) {
            console.log(error)
        } finally {

        }
    }


</script>

<template>
    <PokemonCard />
</template>