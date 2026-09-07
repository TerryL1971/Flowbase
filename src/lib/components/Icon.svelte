<!-- src/lib/components/Icon.svelte -->
<script lang="ts">
	type Props = {
		name: string;
		class?: string;
	};

	let { name, class: klass = 'h-6 w-6' }: Props = $props();

	const paths: Record<string, string> = {
		calendar:
			'M8 2v3M16 2v3M3.5 9.5h17M5 5h14a1.5 1.5 0 0 1 1.5 1.5V19A1.5 1.5 0 0 1 19 20.5H5A1.5 1.5 0 0 1 3.5 19V6.5A1.5 1.5 0 0 1 5 5ZM8 13h3M8 16.5h6',
		users:
			'M16 19v-1.5a3.5 3.5 0 0 0-3.5-3.5h-5A3.5 3.5 0 0 0 4 17.5V19M10 10.5A3.25 3.25 0 1 0 10 4a3.25 3.25 0 0 0 0 6.5ZM20 19v-1.5a3.5 3.5 0 0 0-2.7-3.4M15.5 4.2a3.25 3.25 0 0 1 0 6.1',
		chart: 'M4 20h16M7 20V11M12 20V5M17 20v-6',
		plug: 'M9 3v5M15 3v5M7 8h10v3a5 5 0 0 1-10 0V8ZM12 16v5',
		document:
			'M14 3H7a1.5 1.5 0 0 0-1.5 1.5v15A1.5 1.5 0 0 0 7 21h10a1.5 1.5 0 0 0 1.5-1.5V7.5L14 3ZM13.5 3.5V8h4.5M9 12.5h6M9 16h6',
		check: 'M4.5 12.5l5 5 10-11',
		arrow: 'M5 12h14M13 6l6 6-6 6',
		bolt: 'M13 2 4 14h7l-1 8 9-12h-7l1-8Z',
		shield: 'M12 3 5 6v5c0 4.5 3 8 7 10 4-2 7-5.5 7-10V6l-7-3Z',
		sparkle: 'M12 3v6M12 15v6M3 12h6M15 12h6M6 6l3 3M15 15l3 3M18 6l-3 3M9 15l-3 3'
	};
</script>

<svg
	class={klass}
	viewBox="0 0 24 24"
	fill="none"
	stroke="currentColor"
	stroke-width="1.6"
	stroke-linecap="round"
	stroke-linejoin="round"
	aria-hidden="true"
>
	<path d={paths[name] ?? paths.sparkle} />
</svg>
