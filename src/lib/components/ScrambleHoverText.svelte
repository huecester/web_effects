<script lang="ts">
	export let text: string;
	export let replacementsPerSecond = 30;
	export let cyclesPerLetter = 3;

	let interval: ReturnType<typeof setInterval>;

	function effect(event: MouseEvent | FocusEvent) {
		if (!event.target) return;
		const target = event.target as HTMLElement;

		if (interval) clearInterval(interval);

		let iteration = 0;
		interval = setInterval(() => {
			target.innerText = text
				.split('')
				.map((_, i) => {
					if (i < iteration) {
						return text[i];
					} else {
						return randomChar();
					}
				})
				.join('');

			if (iteration >= text.length) clearInterval(interval);

			iteration += 1 / cyclesPerLetter;
		}, 1000 / replacementsPerSecond);
	}

	function randomChar() {
		const CHARACTERS = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ';
		return CHARACTERS[Math.floor(Math.random() * CHARACTERS.length)];
	}
</script>

<span on:mouseover={effect} on:focus={effect}>{text}</span>
