<!-- src/lib/components/Footer.svelte -->
<script lang="ts">
	const nav = [
		{ href: '#features', label: 'Features' },
		{ href: '#pricing', label: 'Pricing' },
		{ href: '#testimonials', label: 'Customers' },
		{ href: '#demo', label: 'Request a demo' }
	];

	const socials = [
		{
			label: 'X',
			path: 'M4 4l16 16M20 4L4 20'
		},
		{
			label: 'LinkedIn',
			path: 'M6 9v10M6 5.5v.01M11 19v-6a3 3 0 0 1 6 0v6M11 9v10'
		},
		{
			label: 'GitHub',
			path: 'M12 3a9 9 0 0 0-2.8 17.5c.4.1.6-.2.6-.4v-1.6c-2.5.5-3-1.2-3-1.2-.4-1-1-1.3-1-1.3-.8-.6.1-.6.1-.6.9.1 1.4 1 1.4 1 .8 1.4 2.1 1 2.6.8.1-.6.3-1 .6-1.3-2-.2-4.1-1-4.1-4.4 0-1 .3-1.8.9-2.4-.1-.3-.4-1.2.1-2.4 0 0 .8-.3 2.5 1a8.6 8.6 0 0 1 4.6 0c1.7-1.3 2.5-1 2.5-1 .5 1.2.2 2.1.1 2.4.6.6.9 1.4.9 2.4 0 3.4-2.1 4.2-4.1 4.4.3.3.6.9.6 1.8v2.7c0 .2.2.5.6.4A9 9 0 0 0 12 3Z' }
	];
</script>

<footer class="bg-ink-950 pt-16 pb-10">
	<div class="container-page">
		<div class="flex flex-col justify-between gap-10 md:flex-row">
			<div class="max-w-xs">
				<a href="#top" class="flex items-center gap-2 text-white">
					<span
						class="grid h-8 w-8 place-items-center rounded-lg bg-accent-500 text-sm font-extrabold text-white"
						>F</span
					>
					<span class="text-lg font-bold tracking-tight">Flowbase</span>
				</a>
				<p class="mt-4 text-sm text-white/50">
					Project management that respects your team's time.
				</p>
			</div>

			<nav class="flex flex-col gap-3" aria-label="Footer">
				<span class="text-xs font-semibold tracking-widest text-white/40 uppercase">Product</span>
				{#each nav as item (item.href)}
					<a href={item.href} class="text-sm text-white/65 transition-colors hover:text-white"
						>{item.label}</a
					>
				{/each}
			</nav>
		</div>

		<div
			class="mt-12 flex flex-col-reverse items-center justify-between gap-4 border-t border-white/10 pt-6 sm:flex-row"
		>
			<p class="text-xs text-white/40">
				© {new Date().getFullYear()} Flowbase. Fictional product built for a design portfolio.
			</p>
			<div class="flex gap-3">
				{#each socials as s (s.label)}
					<a
						href="/"
						aria-label={s.label}
						class="grid h-9 w-9 place-items-center rounded-lg border border-white/10 text-white/60 transition-colors hover:border-white/25 hover:text-white"
					>
						<svg
							class="h-4 w-4"
							viewBox="0 0 24 24"
							fill="none"
							stroke="currentColor"
							stroke-width="1.6"
							stroke-linecap="round"
							stroke-linejoin="round"
						>
							<path d={s.path} />
						</svg>
					</a>
				{/each}
			</div>
		</div>
	</div>
</footer>
