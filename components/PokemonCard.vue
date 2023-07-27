<script setup>
const { name, apiURL } = defineProps(['name', 'apiURL']);

const { data: pokemon } = await useFetch(
	apiURL,
	{
		key: `pokemon-${name}`,
		transform(data) {
			return {
				name: data.name[0].toUpperCase() + data.name.slice(1),
				//artwork: data.sprites.other['official-artwork']['front_default'],
			};
		},
	}
);

</script>

<template>
	<div>
		<NuxtLink :to="`/pokemon/${name}`">
			<h1>{{ pokemon.name }}</h1>
			<!-- <img :src="pokemon.artwork" /> -->
		</NuxtLink>
	</div>
</template>