<script lang="ts">
	import { browser } from '$app/environment';

	// @ts-ignore
	import rgbHex from 'rgb-hex';
	let useSlider = true;
	let red = 0;
	let green = 0;
	let blue = 0;
	$: hex = `#${rgbHex(red, green, blue)}`;

	// -- BEGIN BOILERPLATE

	let desktop: string;

	if (window.electron && browser) {
		window.electron.receive('from-main', (data: any) => {
			desktop = `Received Message "${data}" from Electron`;
			console.log(desktop);
		});
	}

	const agent = window.electron ? 'Electron' : 'Browser';

	// -- END BOILERPLATE
</script>

<main class="flex flex-col gap-4 w-full h-screen items-center justify-center">
	<div class="w-36 aspect-square rounded-full shadow" style:background-color={hex} />

	<p>{hex}</p>

	<!-- <div class="form-control w-full max-w-xs items-end">
		<label class="label cursor-pointer flex gap-2">
			<span class="label-text">Use slider</span>
			<input type="checkbox" class="toggle toggle-sm" bind:checked={useSlider} />
		</label>
	</div> -->

	<div class="form-control w-full max-w-xs">
		<label class="label" for="red">
			<span class="label-text">Red</span>
			<span class="label-text-alt">{red}</span>
		</label>
		<!-- {#if useSlider} -->
		<input
			type="range"
			min="0"
			max="255"
			bind:value={red}
			class="range range-error"
			name="red"
		/>
		<!-- {:else}
			<input
				type="number"
				min="0"
				max="255"
				bind:value={red}
				class="input input-sm input-error"
				name="red"
			/>
		{/if} -->
	</div>

	<div class="form-control w-full max-w-xs">
		<label class="label" for="green">
			<span class="label-text">Green</span>
			<span class="label-text-alt">{green}</span>
		</label>

		<!-- {#if useSlider} -->
		<input
			type="range"
			min="0"
			max="255"
			bind:value={green}
			class="range range-success"
			name="green"
		/>
		<!-- {:else}
			<input
				type="number"
				min="0"
				max="255"
				bind:value={green}
				class="input input-sm input-success"
				name="green"
			/>
		{/if} -->
	</div>

	<div class="form-control w-full max-w-xs">
		<label class="label" for="blue">
			<span class="label-text">Blue</span>
			<span class="label-text-alt">{blue}</span>
		</label>
		<!-- {#if useSlider} -->
		<input
			type="range"
			min="0"
			max="255"
			bind:value={blue}
			class="range range-info"
			name="blue"
		/>
		<!-- {:else}
			<input
				type="number"
				min="0"
				max="255"
				bind:value={blue}
				class="input input-sm input-info"
				name="blue"
			/>
		{/if} -->
	</div>
</main>

<!-- <style>
	:root {
		font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu,
			Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
	}

	:global(body) {
		margin: 0;
		padding: 0;
	}

	main {
		padding: 2em 1em 1em 1em;
		text-align: center;
		animation: fade 1s;
		margin: 0 auto;
	}

	@keyframes fade {
		from {
			opacity: 0;
		}
		to {
			opacity: 1;
		}
	}
</style> -->
