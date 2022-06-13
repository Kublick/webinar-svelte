<script>
	import { tweened } from 'svelte/motion';
	let original = 15 * 60; // TYPE NUMBER OF SECONDS HERE
	let timer = tweened(original);

	setInterval(() => {
		if ($timer > 0) $timer--;
	}, 1000);

	$: minutes = Math.floor($timer / 60);
	$: minname = minutes > 1 ? 'mins' : 'min';
	$: seconds = Math.floor($timer - minutes * 60);
</script>

<main>
	<div class="flex justify-center gap-2">
		<div class="flex flex-col items-center min-w-18 p-2 text-black lg:p-4">
			<p class="text-xl lg:text-3xl">{minutes}</p>
			<p>{minname}</p>
		</div>
		<div class="flex flex-col items-center min-w-18 p-2 text-black lg:p-4">
			<p class="text-xl lg:text-3xl">{seconds}</p>
			<p>seconds</p>
		</div>
	</div>
	<!-- <progress value={$timer / original} /> -->
</main>

<style>
	main {
		width: 600px;
		margin: 0 auto;
	}
</style>
