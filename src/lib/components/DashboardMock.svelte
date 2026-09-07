<!-- src/lib/components/DashboardMock.svelte -->
<script lang="ts">
	// Purely decorative mock UI — no real data, no screenshots.
	const columns = [
		{
			title: 'In progress',
			cards: [
				{ label: 'Onboarding flow redesign', who: 'AR', tone: 'bg-accent-500' },
				{ label: 'API rate limiting', who: 'JP', tone: 'bg-emerald-500' }
			]
		},
		{
			title: 'Review',
			cards: [{ label: 'Q3 reporting export', who: 'MK', tone: 'bg-amber-500' }]
		},
		{
			title: 'Done',
			cards: [
				{ label: 'Calendar two-way sync', who: 'TL', tone: 'bg-sky-500' },
				{ label: 'Billing page copy', who: 'AR', tone: 'bg-accent-500' }
			]
		}
	];
</script>

<div
	class="mx-auto max-w-5xl overflow-hidden rounded-2xl border border-white/10 bg-ink-900 shadow-2xl shadow-black/50"
>
	<!-- window chrome -->
	<div class="flex items-center gap-2 border-b border-white/10 bg-ink-800 px-4 py-3">
		<span class="h-2.5 w-2.5 rounded-full bg-white/20"></span>
		<span class="h-2.5 w-2.5 rounded-full bg-white/20"></span>
		<span class="h-2.5 w-2.5 rounded-full bg-white/20"></span>
		<span class="ml-3 text-xs text-white/40">Flowbase — Website relaunch</span>
	</div>

	<div class="grid gap-4 p-4 sm:grid-cols-3 sm:p-6">
		{#each columns as col (col.title)}
			<div class="rounded-xl bg-ink-800/60 p-3">
				<div class="mb-3 flex items-center justify-between px-1">
					<span class="text-xs font-semibold tracking-wide text-white/60 uppercase">{col.title}</span>
					<span class="text-xs text-white/30">{col.cards.length}</span>
				</div>
				<div class="flex flex-col gap-2">
					{#each col.cards as card (card.label)}
						<div class="rounded-lg border border-white/10 bg-ink-900 p-3">
							<p class="text-sm text-white/85">{card.label}</p>
							<div class="mt-3 flex items-center justify-between">
								<span class="h-1.5 w-16 rounded-full bg-white/10"></span>
								<span
									class="grid h-6 w-6 place-items-center rounded-full text-[10px] font-bold text-white {card.tone}"
									>{card.who}</span
								>
							</div>
						</div>
					{/each}
				</div>
			</div>
		{/each}
	</div>

	<div class="flex flex-wrap items-center gap-x-6 gap-y-2 border-t border-white/10 px-4 py-3 sm:px-6">
		<span class="text-xs text-white/40">Team load this week</span>
		<div class="flex flex-1 items-center gap-3">
			<div class="h-1.5 flex-1 overflow-hidden rounded-full bg-white/10">
				<div class="h-full w-[68%] rounded-full bg-accent-500"></div>
			</div>
			<span class="text-xs font-medium text-white/60">68%</span>
		</div>
	</div>
</div>
