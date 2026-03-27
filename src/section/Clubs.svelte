<script lang="ts">
	import ClubCard from "../components/ClubCard.svelte";
	import {onMount} from "svelte";

	const clubs = [
		{
			type: "Apprentissage",
			title: "Club Minitalk",
			tags: ["Tout les mardi à 18h", "2h par semaine"],
			video: "/video/demo.mp4",
		},
		{
			type: "Divertissement",
			title: "Club Echecs",
			tags: ["Tout les mardi à 14h", "2h par semaine"],
			video: "/video/demo.mp4",
		},
		{
			type: "Nourriture",
			title: "Club Cuisine",
			tags: ["Tout les mardi à 18h", "2h par semaine"],
			video: "/video/demo.mp4",
		}
	];
	let clubTranslate: number[] = [];

	let section: HTMLElement;

	onMount(() => {
		window.addEventListener("scroll", () => {
			const cards = Array.from(section.children) as HTMLElement[];
			const sectionRect = section.getBoundingClientRect();

			const sectionY = section.offsetTop + (sectionRect.height * ((clubs.length - 1) / clubs.length));

			cards.forEach((card, i) => {
				card.style.zIndex = `${i + 1}`;

				const cardRect = card.getBoundingClientRect();


				const initialTop = card.offsetTop;
				const scrollTop = window.scrollY;
				const offset = initialTop - scrollTop;
				const scale = Math.min(0, offset / cardRect.height);

				if (offset < 40 && sectionY > window.scrollY && i !== cards.length - 1) {
					card.style.transform = `translateY(${40 - offset}px) scale(${Math.max(0, 1 + (scale * 0.1))})`;
					card.style.filter = `blur(${(40 - offset) * 0.025}px)`;
					card.style.opacity = `${Math.max(0, 1 + (scale * 0.8))}`;
					card.style.transformOrigin = 'top';
				} else {
					card.style.transform = "";
				}
			});
		});
	})
</script>

<section class="content" bind:this={section}>
	{#each clubs as club, i}
		<ClubCard
			type={club.type}
			title={club.title}
			tags={club.tags}
			video_src={club.video}
			y={clubTranslate[i] ?? 0}
		/>
	{/each}
</section>

<style lang="scss">
	.content {
		padding: 40px;
		box-sizing: border-box;
		display: flex;
		flex-direction: column;
		gap: 40px;
	}
</style>