<script>
	import LargeTitle from "../components/LargeTitle.svelte";
</script>

<section>
	<div>
		<div class="banner"><LargeTitle text="Evenement"/></div>
		<div class="banner"><LargeTitle text="Good vibes" reverse={true}/></div>
		<div class="banner"><LargeTitle text="Afterworks"/></div>
	</div>
</section>

<style>
	section {
		width: 100%;
		height: 100vh;
		display: flex;
		overflow: hidden;
	}

	section > div {
		flex: 1;
		width: 100%;
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		gap: 60px;
		scale: 1;
	}

	section > div > div {
		padding: 10px 0;
		width: 200vw;
	}

	section > div > div:nth-child(1) {
		background-color: var(--color-pink);
		transform: rotate(3deg);
		z-index: 1;
	}

	section > div > div:nth-child(2) {
		background-color: var(--color-green);
		transform: rotate(-8deg);
		z-index: 2;
	}

	section > div > div:nth-child(3) {
		background-color: var(--color-purple);
		transform: rotate(5deg);
		z-index: 3;
	}
</style>