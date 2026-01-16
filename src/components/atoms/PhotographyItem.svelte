<script lang="ts">
	import { fly } from 'svelte/transition';
	import { cubicOut, quintOut } from 'svelte/easing';
	import { onMount } from 'svelte';

	export let name = '';
	export let tall = false;
	export let subtitle = '';
	export let position = 'center';
	export let commission = false;
	export let basePath = 'photography';

	let open = false;
	let imageUrl: string | null = null;

	const extensions = ['webp', 'jpg', 'jpeg', 'png'];

	function resolveImage() {
		let resolved = false;

		for (const ext of extensions) {
			const safeName = encodeURIComponent(name);
			const url = `/${basePath}/${safeName}.${ext}`;

			const img = new Image();

			img.onload = () => {
				if (!resolved) {
					imageUrl = url;
					resolved = true;
				}
			};

			img.src = url;
		}
	}

	onMount(resolveImage);
</script>

{#if imageUrl}
<button
	class="card"
	class:tall
	style="
		background-image: url('{imageUrl}');
		background-position: {position};
	"
	aria-label={name}
	on:click={() => (open = true)}
/>
{/if}

{#if open && imageUrl}
	<div
		class="modal"
		on:click={() => (open = false)}
		in:fly={{ y: 50, easing: quintOut, duration: 600 }}
		out:fly={{ y: 50, easing: cubicOut, duration: 300 }}
	>
		<h3>{name}</h3>
		<img src={imageUrl} alt={name} />
		{#if subtitle}
			<h6>{subtitle}</h6>
		{/if}
	</div>
{/if}

<style>
	.card {
		background-size: cover;
		background-repeat: no-repeat;
		border-radius: 4px;
		cursor: pointer;
		width: 100%;
		height: 100%;
	}

	.tall {
		grid-row: span 2;
	}

	.modal {
		position: fixed;
		inset: 0;
		background: rgba(0, 0, 0, 0.85);
		backdrop-filter: blur(10px);
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		z-index: 50;
		padding: 20px;
	}

	.modal img {
		max-width: 90vw;
		max-height: 90vh;
		object-fit: contain;
		border-radius: 8px;
		box-shadow: 0 0 20px rgba(0, 0, 0, 0.5);
	}

	h3,
	h6 {
		color: white;
		margin: 10px 0;
		text-align: center;
	}
</style>
