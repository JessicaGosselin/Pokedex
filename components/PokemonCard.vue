<script setup>
const { name } = defineProps(['name']);
</script>

<template>
	<div>
		<NuxtLink :to="`/pokemon/${name}`">{{ name }}</NuxtLink>
	</div>
</template>
