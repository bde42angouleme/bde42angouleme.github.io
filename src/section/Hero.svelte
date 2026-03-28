<script>
</script>
<section>
	<video src="/video/demo.mp4" autoplay loop muted></video>
	<div class="background-overlay"></div>
	<div class="content">
		<h1>On s’occupe de tes <br/> meilleurs souvenirs.</h1>
		<div>
			<p>Le Bureau des Étudiants est une équipe d’étudiants qui propose des événements, des projets et des initiatives pour dynamiser la vie sur le campus.</p>
			<div class="scroll_down">
				{#each { length: 4 } as i}
					<span>
						<svg viewBox="0 0 38 38" xmlns="http://www.w3.org/2000/svg">
							<path d="M38 0V30.0186H35V5.10059L2.12109 38L0 35.877L32.8555 3.00195H8V0H38Z"/>
						</svg>
						Scroll down
						<svg viewBox="0 0 38 38" xmlns="http://www.w3.org/2000/svg">
							<path d="M38 0V30.0186H35V5.10059L2.12109 38L0 35.877L32.8555 3.00195H8V0H38Z"/>
						</svg>
					</span>
				{/each}
			</div>
		</div>
	</div>
</section>

<style>
	@keyframes pulse {
		from {
			transform: translateY(20px);
		}
		to {
			transform: translateY(0);
		}
	}

	section {
		height: 100vh;
		padding: 40px;
		box-sizing: border-box;
		position: relative;
		display: flex;
		flex-direction: column;
		justify-content: flex-end;
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
		background: linear-gradient(0deg, #000 0%, #0000 100%);
		z-index: -1;
	}

	.content {
		display: flex;
		align-items: start;
		gap: 40px;
	}

	h1 {
		font-family: 'Lugati v1', sans-serif;
		text-transform: uppercase;
		margin: 0;
		font-size: 100px;
		margin-bottom: -30px;
	}

	.content > div {
		flex: 1;
		display: flex;
		flex-direction: column;
		gap: 20px;
	}

	.content > div > p {
		font-family: 'Montserrat', sans-serif;
		font-size: 20px;
		margin: 0;
	}

	span {
		position: absolute;
		display: flex;
		align-items: center;
		gap: 20px;
		font-size: 25px;
		text-transform: uppercase;
		animation: pulse 1s cubic-bezier(0.5,0,0,1) infinite alternate;
		margin-bottom: 20px;
	}

	span > svg {
		width: 20px;
		height: 20px;
		rotate: 135deg;
	}

	.scroll_down :nth-child(1) { animation-delay: .09s; color: var(--color-green) }
	.scroll_down :nth-child(1) > svg { fill: var(--color-green) }
	.scroll_down :nth-child(2) { animation-delay: .06s; color: var(--color-pink) }
	.scroll_down :nth-child(2) > svg { fill: var(--color-pink) }
	.scroll_down :nth-child(3) { animation-delay: .03s; color: var(--color-purple) }
	.scroll_down :nth-child(3) > svg { fill: var(--color-purple) }
	.scroll_down :nth-child(4) { animation-delay: .00s; color: var(--color-white) }
	.scroll_down :nth-child(4) > svg { fill: var(--color-white) }

</style>