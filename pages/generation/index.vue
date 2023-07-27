<script setup>
	const { data: generations } = await useFetch(
	`https://pokeapi.co/api/v2/generation`
);
</script>

<template>
	<div>
	<h1>Choose your Generation</h1>
		<nav>
			<NuxtLink v-for="n in generations.count" :to="`/generation/${n}`">Gen {{n}}</NuxtLink>
		</nav>
		<slot />
	</div>
</template>
