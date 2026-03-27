<script lang="ts">
	import {onMount} from "svelte";
	let pointer: HTMLDivElement;
	let expanded = $state(false);
	let mouseX = 0;
	let mouseY = 0;
	let currentX = 0;
	let currentY = 0;

	function animate() {
		currentX += (mouseX - currentX) * (expanded ? 0.15 : 0.1);
		currentY += (mouseY - currentY) * (expanded ? 0.15 : 0.1);

		pointer.style.left = `${currentX - 5}px`;
		pointer.style.top = `${currentY - 5}px`;

		requestAnimationFrame(animate);
	}

	onMount(() => {
		document.addEventListener("mousemove", (e) => {
			mouseX = e.clientX;
			mouseY = e.clientY;
		});

		document.addEventListener("pointerExpand", () => expanded = true);
		document.addEventListener("pointerCollapse", () => expanded = false);

		animate();
	})
</script>

<div id="pointer" class:expanded={expanded} bind:this={pointer}>
	<div>
		<p>Learn more</p>
		<p>Learn more</p>
		<p>Learn more</p>
	</div>
</div>

<style lang="less">
	@keyframes infiniteScroll {
		from {
			transform: translateX(-90px);
		}
		to {
			transform: translateX(0);
		}
	}

	#pointer {
		position: fixed;
		z-index: 1000;
		width: 8px;
		height: 8px;
		border-radius: 4px;
		background-color: var(--color-purple);
		overflow: hidden;
		pointer-events: none;
		transition-property: width, height, transform, border-radius;
		transition-duration: 0.3s;
		display: flex;
		align-items: center;
		justify-content: center;
		gap: 10px;
	}

	#pointer > div {
		width: 100%;
		height: 100%;
		display: flex;
		align-items: center;
		gap: 10px;
		opacity: 0;
		scale: 0;
		transition: .3s;
		animation: infiniteScroll 2s linear infinite;
	}

	#pointer > div > p {
		width: 80px;
		margin: 0;
		white-space: nowrap;
		text-align: center;
		user-select: none;
		transform: translateY(8%);
		transition: 0.3s;
		font-family: 'Lugati v1', sans-serif;
		font-size: 16px;
		text-transform: uppercase;
		letter-spacing: 5%;
	}

	.expanded {
		transform: rotate(-5deg) translateX(-56px) translateY(-16px) !important;
		border-radius: 0 !important;
		width: 120px !important;
		height: 35px !important;
	}

	.expanded > div {
		opacity: 1 !important;
		scale: 1 !important;
	}
</style>