<script>
	import photography from '../../util/photography.json';
	import { browser } from '$app/environment';

	let activeImage = null;

	function scrollToTop() {
		if (browser) {
			window.scrollTo({ top: 0, behavior: 'smooth' });
		}
	}

	function openImage(src, subtitle) {
		activeImage = { src, subtitle };
		if (browser) {
			document.body.style.overflow = 'hidden';
		}
	}

	function closeImage() {
		activeImage = null;
		if (browser) {
			document.body.style.overflow = '';
		}
	}

	function handleKey(e) {
		if (e.key === 'Escape' && activeImage) {
			closeImage();
		}
	}
</script>

<svelte:window on:keydown={handleKey} />

<div class="grid-container">
	<div class="grid">
		{#each photography as { name, tall, subtitle, ext }}
			<div
				class="photo-card {tall ? 'tall' : ''}"
				on:click={() =>
					openImage(
						`/photography/${name}.${ext ?? 'webp'}`,
						subtitle
					)
				}
			>
				<img
					src={`/photography/${name}.${ext ?? 'webp'}`}
					alt={subtitle}
					loading="lazy"
				/>
			</div>
		{/each}
	</div>
</div>

{#if activeImage}
	<div class="lightbox" on:click={closeImage}>
		<img
			src={activeImage.src}
			alt={activeImage.subtitle}
			on:click|stopPropagation
		/>
		<span class="close-btn" on:click|stopPropagation={closeImage}>
			✕
		</span>
	</div>
{/if}

<button
	class="scroll-top"
	on:click={scrollToTop}
	aria-label="Scroll to top"
>
	↑
</button>

<style lang="scss">
	@use '../../styles/mixins.scss' as mixins;

	.grid {
		gap: 0.8rem;
		grid-auto-rows: 200px;
		display: grid;
		grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
		width: 100%;
		max-width: 1400px;
		margin: auto;
	}

	.grid-container {
		display: flex;
		justify-content: center;
	}

	.photo-card {
		overflow: hidden;
		border-radius: 12px;
		cursor: zoom-in;
	}

	.photo-card img {
		width: 100%;
		height: 100%;
		object-fit: cover;
		display: block;
		transition: transform 0.3s ease;
	}

	.photo-card:hover img {
		transform: scale(1.05);
	}

	.photo-card.tall {
		grid-row: span 2;
	}

	.lightbox {
		position: fixed;
		inset: 0;
		background: rgba(0, 0, 0, 0.85);
		backdrop-filter: blur(6px);
		display: flex;
		align-items: center;
		justify-content: center;
		z-index: 999;
	}

	.lightbox img {
		max-width: 92vw;
		max-height: 92vh;
		object-fit: contain;
		border-radius: 14px;
		box-shadow: 0 20px 60px rgba(0, 0, 0, 0.6);
	}

	.close-btn {
		position: absolute;
		top: 1.5rem;
		right: 1.75rem;
		font-size: 2rem;
		color: white;
		cursor: pointer;
	}

	.scroll-top {
		position: fixed;
		right: 1.75rem;
		bottom: 1.75rem;
		width: 52px;
		height: 52px;
		border-radius: 50%;
		background: rgba(0, 0, 0, 0.6);
		color: var(--accent);
		border: 1px solid var(--accent-opacity);
		cursor: pointer;
		z-index: 60;
		display: flex;
		align-items: center;
		justify-content: center;
	}
</style>
