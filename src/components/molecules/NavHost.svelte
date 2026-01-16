<script lang="ts">
	import Nav from '../atoms/Nav.svelte';
	import { fade, scale } from 'svelte/transition';

	let y: number;
	let openMenu = false;

	// Menu close helper
	function closeMenu() {
		openMenu = false;
	}
</script>

<nav>
	<!-- DESKTOP NAV -->
	<div class="desktop" class:scrolled={y > 20}>
		<ul>
			<Nav href="#home" section="/" isSelected={y < 350} />
			<Nav href="#about" section="About" isSelected={y > 350 && y < 675} />
			<Nav href="#pw" section="Work" isSelected={y > 675 && y < 1200} />
			<Nav href="#collab" section="Collaborate" isSelected={y >= 1200} />
		</ul>
	</div>

	<!-- MOBILE HAMBURGER BOTTOM CENTER -->
	<button class="hamburger" on:click={() => (openMenu = true)}>
		<span></span>
		<span></span>
		<span></span>
	</button>

	<!-- MOBILE MODAL -->
	{#if openMenu}
		<div class="overlay" on:click={closeMenu} transition:fade />

		<div class="menuBox" transition:scale>
			<Nav href="#home" section="Home" on:click={() => closeMenu()} />
			<Nav href="#about" section="About" on:click={() => closeMenu()} />
			<Nav href="#pw" section="Work" on:click={() => closeMenu()} />
			<Nav href="#collab" section="Collaborate" on:click={() => closeMenu()} />
		</div>
	{/if}
</nav>

<svelte:window bind:scrollY={y} />

<style lang="scss">
nav { position: relative; }

.desktop {
	position: fixed;
	top: 0;
	z-index: 10;
	padding: 1rem 3rem;
	background: var(--bg-color);
	border-radius: 14px;
	ul { display: flex; gap: 3rem; list-style: none; }
}

.hamburger {
	display: none;
	position: fixed;
	bottom: 1.25rem;
	left: 50%;
	transform: translateX(-50%);
	z-index: 20;
	width: 56px; height: 56px;
	border-radius: 50%;
	background: var(--elevation-one);
	border: none;
	display: flex; flex-direction: column; justify-content: center; gap: 6px;

	span { height: 2px; width: 24px; background: var(--accent); margin: 0 auto; }
}

.overlay {
	position: fixed; inset: 0;
	background: rgba(0,0,0,0.4);
	backdrop-filter: blur(6px);
	z-index: 19;
}

.menuBox {
	position: fixed;
	top: 50%;
	left: 50%;
	transform: translate(-50%, -50%);
	z-index: 20;
	background: var(--bg-color);
	border-radius: 16px;
	padding: 2rem;
	display: flex; flex-direction: column; gap: 1.2rem;
}

@media (max-width: 868px) {
	.desktop { display: none; }
	.hamburger { display: flex; }
}
</style>
