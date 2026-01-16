<script>
	export let color = 'currentColor';
	export let size = 22;
</script>

<svg
	xmlns="http://www.w3.org/2000/svg"
	width={size}
	height={size}
	viewBox="0 0 24 24"
	fill="none"
	stroke={color}
	stroke-width="2"
	stroke-linecap="round"
	stroke-linejoin="round"
>
	<!-- outer square -->
	<rect x="2.5" y="2.5" width="19" height="19" rx="5" ry="5" />

	<!-- inner circle -->
	<circle cx="12" cy="12" r="4.2" />

	<!-- small dot -->
	<circle cx="17.3" cy="6.7" r="1" fill={color} stroke="none" />
</svg>
