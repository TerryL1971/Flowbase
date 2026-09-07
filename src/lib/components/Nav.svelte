<!-- src/lib/components/Nav.svelte -->
<script lang="ts">
	const links = [
		{ href: '#features', label: 'Features' },
		{ href: '#pricing', label: 'Pricing' },
		{ href: '#testimonials', label: 'Customers' }
	];

	let scrolled = $state(false);
	let open = $state(false);

	function onScroll() {
		scrolled = window.scrollY > 8;
	}
</script>

<svelte:window onscroll={onScroll} />

<header
	class="fixed inset-x-0 top-0 z-50 transition-colors duration-300"
	class:bg-ink-950={scrolled}
	class:shadow-lg={scrolled}
	class:shadow-black={scrolled}
>
	<nav class="container-page flex h-16 items-center justify-between">
		<a href="#top" class="flex items-center gap-2 text-white">
			<span
				class="grid h-8 w-8 place-items-center rounded-lg bg-accent-500 text-sm font-extrabold text-white"
				>F</span
			>
			<span class="text-lg font-bold tracking-tight">Flowbase</span>
		</a>

		<div class="hidden items-center gap-8 md:flex">
			{#each links as link (link.href)}
				<a
					href={link.href}
					class="text-sm font-medium text-white/70 transition-colors hover:text-white"
					>{link.label}</a
				>
			{/each}
			<a
				href="#demo"
				class="rounded-lg bg-accent-500 px-4 py-2 text-sm font-semibold text-white transition-colors hover:bg-accent-600"
				>Request a demo</a
			>
		</div>

		<button
			class="rounded-lg p-2 text-white md:hidden"
			aria-label="Toggle menu"
			aria-expanded={open}
			onclick={() => (open = !open)}
		>
			<svg class="h-6 w-6" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
				{#if open}
					<path d="M6 6l12 12M18 6 6 18" stroke-linecap="round" />
				{:else}
					<path d="M4 7h16M4 12h16M4 17h16" stroke-linecap="round" />
				{/if}
			</svg>
		</button>
	</nav>

	{#if open}
		<div class="border-t border-white/10 bg-ink-950 md:hidden">
			<div class="container-page flex flex-col gap-1 py-3">
				{#each links as link (link.href)}
					<a
						href={link.href}
						class="rounded-lg px-2 py-2 text-sm font-medium text-white/80 hover:bg-white/5"
						onclick={() => (open = false)}>{link.label}</a
					>
				{/each}
				<a
					href="#demo"
					class="mt-1 rounded-lg bg-accent-500 px-2 py-2 text-center text-sm font-semibold text-white"
					onclick={() => (open = false)}>Request a demo</a
				>
			</div>
		</div>
	{/if}
</header>
