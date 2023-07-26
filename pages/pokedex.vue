<script setup>
const query = ref('');
const pokemons = ref([]);
const pokemon = ref([]);

const { results } = await $fetch(
	`https://pokeapi.co/api/v2/pokemon?offset=0&limit=10000`
);
pokemons.value = results;

async function search() {
	const { id, name } = await $fetch(
		`https://pokeapi.co/api/v2/pokemon/${query.value}`
	);
	pokemon.value.id = id;
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

		<PokemonCard :name="pokemon.name"></PokemonCard>

		<ul>
			<PokemonCard
				v-for="pokemon in pokemons"
				:name="pokemon.name"
			></PokemonCard>
		</ul>
	</div>
</template>
