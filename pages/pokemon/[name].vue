<script setup>
const route = useRoute();

const { data } = await useFetch(
	`https://pokeapi.co/api/v2/pokemon/${route.params.name}`,
	{
		key: `/pokemon/${route.params.name}`,
		transform(data) {
			return {
				name: data.name[0].toUpperCase() + data.name.slice(1),
				sprite: data.sprites.front_default,
			};
		},
	}
);
</script>

<template>
	<div>
		<h1>{{ data.name }}</h1>
		<img :src="data.sprite" />
	</div>
</template>
