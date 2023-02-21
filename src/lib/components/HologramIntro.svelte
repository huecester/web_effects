<script lang="ts">
	export const prerender = false;
	export const ssr = false;

	export let color: string;

	let div: HTMLDivElement;

	$: div?.style.setProperty('--color', color);
</script>

<div bind:this={div}>
	<slot />
</div>

<style lang="scss">
	$hologram-delay: 500ms;
	$hologram-duration: 450ms;
	$flicker-delay: 125ms;
	$flicker-duration: 400ms;

	div {
		width: fit-content;
		position: relative;
		color: rgba(0, 0, 0, 0);
		animation: $flicker-duration flicker ($flicker-delay + $hologram-delay + $hologram-duration)
			linear forwards;
	}

	div::before {
		content: '';
		position: absolute;
		top: 0;
		left: 0;
		width: 100%;
		height: 100%;
		background-color: var(--color);
		transform: scaleY(0);
		transform-origin: top;
		animation: $hologram-duration hologram $hologram-delay cubic-bezier(0.78, 0.18, 0.21, 0.82)
			forwards;
	}

	@keyframes hologram {
		from,
		to {
			transform: scaleY(0);
		}

		50% {
			transform: scaleY(65%);
		}

		to {
			transform-origin: bottom;
		}
	}

	@keyframes flicker {
		from,
		30%,
		70% {
			color: rgba(0, 0, 0, 0);
		}

		10%,
		50%,
		to {
			color: inherit;
		}
	}
</style>
