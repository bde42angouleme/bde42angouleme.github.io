<script lang="ts">
	let { text, link } = $props<{text: string, link: string}>();
</script>

<a href={link}>
	<span class="hover_circle"><img src="/img/arrow.svg" alt="arrow"/></span>
	<div class="text">{text}</div>
	<span class="circle"><img src="/img/arrow.svg" alt="arrow"/></span>
</a>

<style>
	a {
		height: 50px;
		display: flex;
		align-items: center;
		text-decoration: none;
		--transition: .4s cubic-bezier(0.5,0,0,1)
	}

	img {
		width: 16px;
		height: 16px;
		transition: var(--transition);
	}

	.hover_circle > img {
		filter: invert();
	}

	.hover_circle {
		display: flex;
		width: 0;
		height: 0;
		align-items: center;
		justify-content: center;
		background-color: var(--color-green);
		border-radius: 50px;
		overflow: hidden;
		transition: var(--transition);
	}

	a:hover > .hover_circle {
		width: 50px;
		height: 50px;
		transform: rotate(45deg);
	}

	a > .hover_circle > img {
		scale: 0;
	}

	a:hover > .hover_circle > img {
		scale: 1;
	}

	a:hover > .circle {
		width: 0;
		height: 0;
		transform: rotate(45deg);
	}

	a > .circle > img {
		scale: 1;
	}

	a:hover > .circle > img {
		scale: 0;
	}

	.circle {
		display: flex;
		width: 50px;
		height: 50px;
		align-items: center;
		justify-content: center;
		background-color: var(--color-purple);
		border-radius: 50px;
		overflow: hidden;
		transition: var(--transition);
	}

	.text {
		display: flex;
		align-items: center;
		justify-content: center;
		background-color: var(--color-white);
		color: var(--color-black);
		height: 50px;
		border-radius: 50px;
		padding: 0 15px;
	}
</style>