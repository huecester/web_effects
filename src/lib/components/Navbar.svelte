<script lang="ts">
	import '@fontsource/space-mono';
	import HologramIntro from './HologramIntro.svelte';
	import ScrambleHoverText from './ScrambleHoverText.svelte';

	export let links: { name: string; href: string }[];
</script>

<nav>
	<ul>
		{#each links as { name, href }}
			<li>
				<a {href}>
					<ScrambleHoverText text={name} />
				</a>
			</li>
		{/each}
	</ul>
</nav>

<div class="hologram-intro">
	<HologramIntro color="white">Hello, world!</HologramIntro>
</div>

<style lang="scss">
	nav {
		ul {
			margin: 0;
			padding: 0;

			li {
				list-style-type: none;

				a {
					font-size: 5rem;
					font-weight: bold;
					text-transform: uppercase;

					color: inherit;
					text-decoration: inherit;
				}
			}
		}
	}

	.hologram-intro {
		background-color: black;
		font-size: 5rem;
	}
</style>
