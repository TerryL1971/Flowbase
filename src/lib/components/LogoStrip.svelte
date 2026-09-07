<!-- src/lib/components/LogoStrip.svelte -->
<script lang="ts">
	// Generic, clearly fictional wordmarks — not real companies.
	const wordmarks = ['Northwind', 'Aperture', 'Loomly', 'Basecliff', 'Vantage', 'Quorum'];
</script>

<section class="border-b border-slatey-100 bg-white py-12">
	<div class="container-page">
		<p class="text-center text-xs font-semibold tracking-widest text-ink-900/40 uppercase">
			Trusted by teams at
		</p>
		<div
			class="mt-6 flex flex-wrap items-center justify-center gap-x-10 gap-y-4 sm:gap-x-14"
			aria-label="Customer logos (illustrative)"
		>
			{#each wordmarks as name (name)}
				<span
					class="text-lg font-bold tracking-tight text-ink-900/35 transition-colors hover:text-ink-900/55"
					>{name}</span
				>
			{/each}
		</div>
	</div>
</section>
