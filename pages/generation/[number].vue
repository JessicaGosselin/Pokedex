<script setup>
const route = useRoute();

const genNumber = route.params.number;
const { data: generation } = await useFetch(
	`https://pokeapi.co/api/v2/generation/${route.params.number}`
);

generation.value.pokemon_species.sort(sortFunction);

function sortFunction(a, b) {
	let a_id = +a.url.replace('https://pokeapi.co/api/v2/pokemon-species/', '').replace('/', '');
	let b_id = +b.url.replace('https://pokeapi.co/api/v2/pokemon-species/', '').replace('/', '');
    return (a_id < b_id) ? -1 : 1;
}

</script>

<template>
	<div>
		<h1>Generation {{ route.params.number }}</h1>

		<div class="pokedex">
			<div v-for="pokemon in generation.pokemon_species">
				<PokemonCard :name="pokemon.name"/>
			</div>
		</div>
	</div>
</template>
