<template>
	<div>
		<nav>
			<NuxtLink to="/pokedex">Pokedex</NuxtLink>
			<NuxtLink to="/generation">Generations</NuxtLink>
		</nav>
		<slot />
	</div>
</template>

<style>
	nav {
		display: flex;
		gap: 15px;
	}
</style>
