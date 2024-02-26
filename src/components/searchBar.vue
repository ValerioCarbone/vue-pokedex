<template>
    <div class="search-bar">
        <input type="search" name="" id="" placeholder="Pikachu" v-model="query">
        <button @click="fetchPokemon">Search</button>
    </div>
    <div>
        {{ pokemonName }}
    </div>
</template>

<script>
export default {

    data() {
        return {
            url: 'https://pokeapi.co/api/v2/pokemon/',
            query: null,
            pokemonName: null,
        }
    },
    methods: {
        fetchPokemon() {
            if (this.query != null) {
                fetch(`${this.url}${this.query}`)
                    .then(response => {
                        return response.json();
                    }).then(data => {
                        this.pokemonName = data.name
                    });
            }


        }
    }
}
</script>

<style lang="scss" scoped></style>