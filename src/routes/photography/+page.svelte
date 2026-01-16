<script>
	import NavHost from '../../components/molecules/NavHost.svelte';
	import PhotographyGrid from '../../components/molecules/PhotographyGrid.svelte';
	import Footer from '../../components/molecules/Footer.svelte';
</script>

<NavHost />

<main class="photo-page">
	<h1>Photography</h1>

	<!-- 🔥 IMPORTANT: PhotographyGrid, NOT ArtGrid -->
	<PhotographyGrid />
</main>

<Footer />

<style>
	.photo-page {
		padding: 6rem 1rem 3rem; /* header se neeche push */
		max-width: 1400px;
		margin: auto;
	}

	h1 {
		text-align: center;
		margin-bottom: 3rem;
		font-size: 2.5rem;
	}
</style>
