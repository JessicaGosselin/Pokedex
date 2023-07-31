<script setup>
const route = useRoute();
const pokemon = ref([]);

const genNumber = route.params.number;
const { data: generation } = await useFetch(
	`https://pokeapi.co/api/v2/generation/${route.params.number}`
);

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
