<script lang="ts">
	import '@fontsource/space-mono';
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

<style lang="scss">
	nav {
		font-family: 'Space Mono', monospace;
		background-color: black;

		ul {
			margin: 0;
			padding: 0;

			li {
				list-style-type: none;

				a {
					font-size: 5rem;
					font-weight: bold;
					color: white;
					text-transform: uppercase;
					text-decoration: none;
				}
			}
		}
	}
</style>
