<script lang="ts">
	import PointerExpand from "../components/PointerExpand.svelte";

	const events = [
		{
			title: "Galette au sarrasin",
			tags: ["Nourriture", "Mardi de 12h00 à 13h30"]
		},
		{
			title: "Galette au sarrasin",
			tags: ["Nourriture", "Mardi de 12h00 à 13h30"]
		},
		{
			title: "Galette au sarrasin",
			tags: ["Nourriture", "Mardi de 12h00 à 13h30"]
		}
	];
</script>

<section>
	{#each events as event, i}
		<PointerExpand>
			<a class="event" href="#" class:last={i === events.length - 1}>
				<div>
					<h3>{event.title}</h3>
					<div class="tags">
						{#each event.tags as tag}
							<span>{tag}</span>
						{/each}
					</div>
				</div>
				<img src="/img/link.svg" alt="arrow"/>
			</a>
		</PointerExpand>
	{/each}
</section>

<style>
	section {
		min-height: 100vh;
		display: flex;
		flex-direction: column;
		box-sizing: border-box;
		padding: 40px;
	}

	.event {
		box-sizing: border-box;
		height: 170px;
		border-top: 1px solid var(--color-white);
		display: flex;
		align-items: center;
		padding: 0 20px;
		transition: .3s;
		text-decoration: none;
		color: var(--color-white);
	}

	.last {
		border-bottom: 1px solid var(--color-white);
	}

	.event:hover {
		padding: 0 60px;
		background-color: var(--color-pink);
	}

	.event > img {
		width: 50px;
		height: 50px;
		transition: .3s;
	}

	.event:hover > img {
		transform: rotate(45deg);
	}

	.event > div {
		flex: 1;
	}

	.event > div > h3 {
		margin: 0;
		font-family: 'Lugati v1', sans-serif;
		text-transform: uppercase;
		font-size: 60px;
	}

	.event > div > .tags {
		display: flex;
		align-items: center;
		gap: 10px;
	}

	.event > div > .tags > span {
		padding: 5px 20px;
		border-radius: 20px;
		background-color: var(--color-purple);
	}
</style>