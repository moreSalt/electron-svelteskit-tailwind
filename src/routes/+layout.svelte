<script lang="ts">
	import { onMount } from 'svelte';
	// import '$app.css';
	let ready: boolean = false;
	onMount(() => (ready = true));
</script>

<div class="dragbar" />

{#if ready}
	<slot />
{/if}

<style>
	.dragbar {
		-webkit-app-region: drag;
		position: absolute;
		z-index: 100;
		height: 40px;
		width: 100%;
	}
	@tailwind base;
	@tailwind components;
	@tailwind utilities;
</style>
