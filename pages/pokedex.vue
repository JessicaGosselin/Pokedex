<script setup>
const query = ref('');
const pokemon = ref([]);

const { data: pokemons } = await useFetch(
	`https://pokeapi.co/api/v2/pokemon?offset=0&limit=10000`
);

async function search() {
	const { name } = await $fetch(
		`https://pokeapi.co/api/v2/pokemon/${query.value}`
	);
	pokemon.value.name = name;
}
</script>

<template>
	<div>
		<h1>POKEDEX</h1>

		<form @submit.prevent="search">
			<input type="text" v-model="query" />
			<button>Who's that Pokemon?</button>
		</form>

		<PokemonCard v-if="pokemon.name" :name="`${pokemon.name}`" />

		<ul>
			<PokemonCard
				v-for="pokemon in pokemons.results"
				:name="pokemon.name"
			/>
		</ul>
	</div>
</template>
