<script lang="ts">
	import Nav from '../atoms/Nav.svelte';
	let y: number;
</script>

<nav>
	<div class:scrolled={y > 20}>
		<ul>
			<Nav href="#home" section="/" isSelected={y < 350}>
				<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" fill="var(--accent)" viewBox="0 0 24 24">
					<path d="M10 20v-6h4v6h5v-8h3L12 3 2 12h3v8z" />
				</svg>
			</Nav>

			<Nav href="#about" section="About" isSelected={y > 350 && y < 675}>
				<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" fill="var(--accent)" viewBox="0 0 24 24">
					<path d="M12 2a10 10 0 100 20 10 10 0 000-20zm1 15h-2v-6h2v6zm0-8h-2V7h2v2z" />
				</svg>
			</Nav>

			<Nav href="#pw" section="Work" isSelected={y > 675 && y < 1200}>
				<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" fill="var(--accent)" viewBox="0 0 24 24">
					<path d="M20 6h-4V4a2 2 0 00-2-2h-4a2 2 0 00-2 2v2H4a2 2 0 00-2 2v11a2 2 0 002 2h16a2 2 0 002-2V8a2 2 0 00-2-2z" />
				</svg>
			</Nav>

			<Nav href="#collab" section="Collaborate" isSelected={y >= 1200}>
				<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" fill="var(--accent)" viewBox="0 0 24 24">
					<path d="M16 11c1.66 0 2.99-1.34 2.99-3S17.66 5 16 5s-3 1.34-3 3 1.34 3 3 3zM8 11c1.66 0 2.99-1.34 2.99-3S9.66 5 8 5 5 6.34 5 8s1.34 3 3 3zm0 2c-2.33 0-7 1.17-7 3.5V19h14v-2.5C15 14.17 10.33 13 8 13zm8 0c-.29 0-.62.02-.97.05 1.16.84 1.97 1.97 1.97 3.45V19h6v-2.5c0-2.33-4.67-3.5-7-3.5z"/>
				</svg>
			</Nav>
		</ul>
	</div>
</nav>

<svelte:window bind:scrollY={y} />

<style lang="scss">
nav {
	max-width: 100vw;
	overflow-x: hidden;
}

/* NAV BAR */
div {
	position: fixed;
	top: 0;
	z-index: 999;

	display: flex;
	justify-content: center;
	align-items: center;

	width: fit-content;
	padding: 1.25rem 3rem;

	background-color: var(--bg-color);
	backdrop-filter: blur(15px);
	border-radius: 14px;
	transition: all 0.3s ease;

	ul {
		display: flex;
		gap: clamp(2rem, 4vw, 4rem);
		margin: 0;
		padding: 0;
		list-style: none;
	}
}

.scrolled {
	padding: 0.75rem 3rem;
	background-color: var(--elevation-five);
	box-shadow: 0 15px 20px rgba(0, 0, 0, 0.35);
}

/* 🔥 MOBILE FINAL FIX */
@media (max-width: 868px) {
	div {
		top: auto;
		bottom: env(safe-area-inset-bottom);
		left: 0;

		width: 100%;
		height: 64px;

		padding: 0;
		border-radius: 0;
		background-color: var(--elevation-one);
	}

	div ul {
		width: 100%;
		height: 100%;
		padding: 0 1rem;
		justify-content: space-between;
		align-items: center;
		box-sizing: border-box;
	}
}
</style>
