<script>
	import PhotographyGrid from '../../components/molecules/PhotographyGrid.svelte';
	import Tooltip from '../atoms/Tooltip.svelte';
	import { goto } from '$app/navigation';
</script>

<section>
	<div class="wrapper" id="pw">
		<Tooltip tip="Click on a photograph">
			<h2><span>Photography</span> Work</h2>
		</Tooltip>
	</div>

	<div class="art-wrapper">
		<PhotographyGrid />

		<div class="fade-overlay"></div>

		<button class="show-more" on:click={() => goto('/photography')}>
			Show More
		</button>
	</div>
</section>

<style lang="scss">
	section {
		padding-top: 3rem;
		margin-bottom: 6rem; /* 🔑 THIS FIXES OVERLAP */
	}

	span {
		color: var(--accent);
	}

	h2 {
		margin-bottom: 1rem;
		text-align: center;
	}

	.wrapper {
		display: flex;
		justify-content: center;
	}

	.art-wrapper {
		position: relative;
		max-height: 520px;
		overflow: hidden;
	}

	.fade-overlay {
		position: absolute;
		bottom: 0;
		left: 0;
		width: 100%;
		height: 25%;
		background: linear-gradient(
			to bottom,
			rgba(0, 0, 0, 0) 0%,
			rgba(0, 0, 0, 0.85) 100%
		);
		z-index: 2;
		pointer-events: none;
	}

	.show-more {
		position: absolute;
		bottom: 25px;
		left: 50%;
		transform: translateX(-50%);
		padding: 0.9rem 2rem;
		border-radius: 16px;
		border: none;
		cursor: pointer;
		background: var(--accent);
		color: white;
		z-index: 3;
	}
</style>
