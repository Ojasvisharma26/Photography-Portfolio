<script lang="ts">
	import { onMount, onDestroy } from 'svelte';

	let name = '@26_Ojasvi';
	let location = 'New Delhi, India';
	let time = '';

	let interval: ReturnType<typeof setInterval>;

	function updateTime() {
		time = new Date().toLocaleTimeString('en-IN', {
			timeZone: 'Asia/Kolkata',
			hour: '2-digit',
			minute: '2-digit',
			second: '2-digit',
			hour12: true
		});
	}

	onMount(() => {
		updateTime();
		interval = setInterval(updateTime, 1000);
	});

	onDestroy(() => {
		clearInterval(interval);
	});
</script>

<h2>activity</h2>

<div class="contain">
	<img src="default.webp" alt="profile" class="big" />

	<div>
		<h3>{name}</h3>
		<h5>{location}</h5>
		<h5>{time}</h5>
	</div>
</div>

<style lang="scss">
	.contain {
		display: flex;
		gap: 2.25rem;
		align-items: center;
	}

	h2 {
		display: none;
	}

	.big {
		height: 135px;
		width: 135px;
		border-radius: 20px;
		user-select: none;
	}

	@media screen and (max-width: 868px) {
		h2 {
			display: block;
			margin-bottom: 1rem;
		}

		.big {
			height: 100px;
			width: 100px;
			border-radius: 17px;
		}
	}
</style>
