<script lang="ts">
	import PointerExpand from "./PointerExpand.svelte";

	let { type, title, tags, video_src, y } =
			$props<{ type: string, title: string, tags: string[], video_src: string, y: number }>();
</script>

<PointerExpand>
	<div class="card">
		<video src={video_src} autoplay loop muted></video>
		<div class="background-overlay"></div>
		<span class="type">{type}</span>
		<h3>{title}</h3>
		<div class="tags">
			{#each tags as tag}
				<span class="tag">{tag}</span>
			{/each}
		</div>
	</div>
</PointerExpand>

<style lang="scss">
	.card {
		width: calc(100vw - 80px);
		height: calc(100vh - 80px);
		border-radius: 20px;
		overflow: hidden;
		position: relative;
		padding: 30px;
		box-sizing: border-box;
		display: flex;
		flex-direction: column;
		justify-content: flex-end;
		align-items: start;
	}

	video {
		position: absolute;
		top: 0;
		left: 0;
		width: 100%;
		height: 100%;
		object-fit: cover;
		z-index: -1;
	}

	.background-overlay {
		position: absolute;
		top: 0;
		left: 0;
		width: 100%;
		height: 100%;
		background: linear-gradient(0deg, #000C 0%, #0000 100%);
		z-index: -1;
	}

	.type {
		padding: 8px 10px;
		font-family: "Montserrat", sans-serif;
		font-weight: 600;
		text-transform: uppercase;
		background-color: var(--color-green);
		color: var(--color-black);
		margin-bottom: 12px;
	}

	h3 {
		font-family: 'Lugati v1', sans-serif;
		font-size: 120px;
		text-transform: uppercase;
		margin: 0;
	}

	.tags {
		display: flex;
		gap: 10px;
		margin-top: -10px;
	}

	.tag {
		padding: 8px 16px;
		font-family: "Montserrat", sans-serif;
		font-weight: 500;
		background-color: #FD84FE;
		border-radius: 100px;
		backdrop-filter: blur(20px);
		border: 1px solid #0001;
	}
</style>