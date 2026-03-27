<script lang="ts">
	import {onMount} from "svelte";

	let { text, reverse = false } = $props<{text: string, reverse?: boolean}>();
	let repeatElement: HTMLDivElement;
	let startPos = $state(0);
	let endPos = $state(0);

	onMount(() => {
		startPos = reverse ? 0 : (repeatElement.getBoundingClientRect().width * -1) - 40;
		endPos = reverse ? (repeatElement.getBoundingClientRect().width * -1) - 40 : 0;
	})
</script>

<div class="container" style={`--start-pos: ${startPos}px; --end-pos: ${endPos}px;`}>
	<div class="large-title" style={``}>
		{#each { length: 6 } as i}
			<div class="repeat" bind:this={repeatElement}>
				<h2>{text}</h2>
				<img src="/img/eyes.png" alt="eyes"/>
			</div>
		{/each}
	</div>
</div>

<style>
	@keyframes infiniteScroll {
		from {
			transform: translateX(var(--start-pos));
		}
		to {
			transform: translateX(var(--end-pos));
		}
	}

	.container {
		width: 100%;
		height: 155px;
		overflow: hidden;
		display: flex;
		align-items: center;
	}

	.large-title {
		display: flex;
		align-items: center;
		gap: 40px;
		animation: infiniteScroll 4s linear infinite;
	}

	.repeat {
		display: flex;
		align-items: center;
		gap: 40px;
		transform: translateY(15px);
	}

	h2 {
		font-family: 'Lugati v1', sans-serif;
		text-transform: uppercase;
		font-size: 140px;
		white-space: nowrap;
		margin: 0;
	}

	img {
		height: 140px;
		width: 140px;
		transform: translateY(-15px);
	}
</style>