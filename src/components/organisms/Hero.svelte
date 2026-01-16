<script>
	import HeroImage from '../../components/atoms/HeroImage.svelte';
	import Button from '../atoms/Button.svelte';
	import Socials from '../molecules/Socials.svelte';

	function handleClick() {
		const el = document.querySelector('#about');
		if (!el) return;
		el.scrollIntoView({ behavior: 'smooth' });
	}

	function scrollToTop() {
		window.scrollTo({ top: 0, behavior: 'smooth' });
	}
</script>

<section id="home" class="wrapper">
	<div>
		<h1>Ojasvi Sharma</h1>
		<h4>
			Documenting people, places, and everyday stories through honest, thoughtful frames, focusing on light, emotion, and moments that often go unnoticed.
		</h4>

		<div class="socials">
			<Socials />
		</div>

		<Button side on:click={handleClick}>
			Discover my work ↓
		</Button>
	</div>

	<HeroImage />
</section>

<!-- 🔥 SCROLL TO TOP BUTTON -->
<button class="scroll-top" on:click={scrollToTop} aria-label="Scroll to top">
	↑
</button>

<section id="about" class="section-title">
	<h2 class="section-heading">
		<span class="about-dark">About</span>
		<span class="about-light">Me</span>
	</h2>
</section>

<style lang="scss">
	@use '../../styles/mixins.scss' as mixins;

	.wrapper {
		scroll-margin-top: 20rem;
		display: flex;
		justify-content: space-between;
		align-items: center;
		margin-bottom: 5.75rem;
		margin-top: 7rem;
	}

	.socials {
		margin-top: 1rem;
		margin-bottom: 1.7rem;
	}

	h4 {
		margin-top: 1rem;
	}

	h1::before {
		@include mixins.outlineText(
			$content: '///',
			$translateX: -95%,
			$letterSpacing: -0.1em
		);
	}

	.section-title {
		width: 100vw;
		display: flex;
		justify-content: center;
		margin: 6rem 0 3rem;
	}

	.section-heading {
		color: var(--accent);
	}

	.section-heading .about-dark {
		color: var(--text-primary);
	}

	/* 🔥 FLOATING SCROLL TO TOP BUTTON */
	.scroll-top {
		position: fixed;
		right: 1.75rem;
		bottom: 1.75rem;
		width: 52px;
		height: 52px;
		border-radius: 50%;

		background: rgba(0, 0, 0, 0.6);
		backdrop-filter: blur(10px);
		-webkit-backdrop-filter: blur(10px);

		color: var(--accent);
		font-size: 1.3rem;
		font-weight: 700;

		border: 1px solid var(--accent-opacity);
		cursor: pointer;
		z-index: 50;

		display: flex;
		align-items: center;
		justify-content: center;

		transition: transform 0.25s ease, box-shadow 0.25s ease, background 0.25s ease;
	}

	.scroll-top:hover {
		transform: translateY(-6px);
		box-shadow: 0 10px 30px rgba(0, 0, 0, 0.45);
		background: rgba(0, 0, 0, 0.75);
	}
</style>
