<!-- src/lib/components/Hero.svelte -->
<script lang="ts">
	import { fly } from 'svelte/transition';
	import DashboardMock from './DashboardMock.svelte';
</script>

<section id="top" class="relative overflow-hidden bg-ink-950 pt-28 pb-20 sm:pt-36 sm:pb-28">
	<!-- ambient glow -->
	<div
		class="pointer-events-none absolute -top-40 left-1/2 h-[38rem] w-[38rem] -translate-x-1/2 rounded-full bg-accent-600/25 blur-[120px]"
		aria-hidden="true"
	></div>
	<div
		class="pointer-events-none absolute top-40 -right-40 h-[24rem] w-[24rem] rounded-full bg-accent-400/15 blur-[110px]"
		aria-hidden="true"
	></div>

	<div class="container-page relative">
		<div class="mx-auto max-w-3xl text-center">
			<span
				class="inline-flex items-center gap-2 rounded-full border border-white/15 bg-white/5 px-3 py-1 text-xs font-medium text-white/80"
			>
				<span class="h-1.5 w-1.5 rounded-full bg-accent-400"></span>
				New: capacity-aware auto scheduling
			</span>

			<h1
				class="mt-6 text-4xl font-extrabold tracking-tight text-white sm:text-5xl md:text-6xl"
				in:fly={{ y: 16, duration: 500 }}
			>
				Project management that
				<span class="text-accent-400"> respects your team's time</span>
			</h1>

			<p
				class="mx-auto mt-6 max-w-2xl text-lg text-white/70"
				in:fly={{ y: 16, duration: 500, delay: 80 }}
			>
				Flowbase plans the work, balances the load, and keeps everyone in sync — so small teams
				ship on schedule without burning out.
			</p>

			<div
				class="mt-9 flex flex-col items-center justify-center gap-3 sm:flex-row"
				in:fly={{ y: 16, duration: 500, delay: 160 }}
			>
				<a
					href="#demo"
					class="w-full rounded-xl bg-accent-500 px-6 py-3 text-center text-sm font-semibold text-white shadow-lg shadow-accent-700/40 transition-colors hover:bg-accent-600 sm:w-auto"
					>Request a demo</a
				>
				<a
					href="#pricing"
					class="w-full rounded-xl border border-white/20 px-6 py-3 text-center text-sm font-semibold text-white transition-colors hover:bg-white/5 sm:w-auto"
					>See pricing</a
				>
			</div>

			<p class="mt-4 text-xs text-white/45">14-day trial · No credit card required</p>
		</div>

		<div class="mt-16 sm:mt-20" in:fly={{ y: 28, duration: 600, delay: 220 }}>
			<DashboardMock />
		</div>
	</div>
</section>
