<script setup>
const { name } = defineProps(['name']);

const { data: pokemon } = await useFetch(
	`https://pokeapi.co/api/v2/pokemon/${name}`,
	{
		key: `pokemon-${name}`,
		transform(data) {
			return {
				name: data.name[0].toUpperCase() + data.name.slice(1),
				artwork: data.sprites.other['official-artwork']['front_default'],
			};
		},
	}
);

</script>

<template>
	<div>
		<NuxtLink :to="`/pokemon/${name}`">
			<h1>{{ pokemon.name }}</h1>
			<img :src="pokemon.artwork" />
		</NuxtLink>
	</div>
</template>