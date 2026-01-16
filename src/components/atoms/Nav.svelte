<script lang="ts">
	import { createEventDispatcher } from 'svelte';

	export let href = '#';
	export let section = 'home';
	export let isSelected = false;

	const dispatch = createEventDispatcher();

	function handleClick() {
		const el = document.querySelector(href);
		if (el) {
			el.scrollIntoView({ behavior: 'smooth', block: 'start' });
		}

		// 🔥 CORRECT WAY TO TELL PARENT
		dispatch('select');
	}
</script>

<li class:selected={isSelected}>
	<button on:click={handleClick}>
		<div class="icon-container">
			<slot />
		</div>
		<h5>{section}</h5>
	</button>
</li>

<style lang="scss">
li {
	list-style: none;
}

button {
	background: transparent;
	border: none;
	color: var(--text-secondary);
	font-size: 1.1rem;
	cursor: pointer;

	display: flex;
	align-items: center;
	gap: 0.75rem;

	padding: 13px 25px;
	border-radius: 100px;
	transition: background-color 0.3s;
}

button:hover {
	background-color: var(--elevation-four);
}

h5 {
	opacity: 0.8;
	transition: 0.3s;
}

.selected h5,
button:hover h5 {
	color: var(--text-primary);
	opacity: 1;
}

.icon-container {
	display: none;
}

@media (max-width: 868px) {
	button {
		flex-direction: column;
		font-size: 0.9rem;
	}

	.icon-container {
		display: block;
		padding: 6px 24px;
		border-radius: 100px;
	}
}
</style>
