<!-- src/lib/components/Testimonials.svelte -->
<script lang="ts">
	// Original placeholder quotes — fictional people and teams.
	const quotes = [
		{
			quote:
				'We stopped doing the Monday “who has bandwidth” call. Flowbase already knows, and the schedule reflects it.',
			name: 'Dana Whitfield',
			role: 'Operations Lead, Northwind Studio'
		},
		{
			quote:
				'Onboarding a new designer used to mean a week of “where does this live?” Now they open one task and the whole history is right there.',
			name: 'Marcus Iyer',
			role: 'Design Manager, Aperture Labs'
		},
		{
			quote:
				'The weekly report writes itself. I forward it to the client Friday afternoon and my status meeting is basically over before it starts.',
			name: 'Priya Constantine',
			role: 'Project Director, Basecliff'
		}
	];
</script>

<section id="testimonials" class="bg-white py-20 sm:py-28">
	<div class="container-page">
		<div class="mx-auto max-w-2xl text-center">
			<span class="text-sm font-semibold tracking-wide text-accent-600 uppercase">Customers</span>
			<h2 class="mt-3 text-3xl font-extrabold tracking-tight text-ink-900 sm:text-4xl">
				Teams that got their week back
			</h2>
		</div>

		<div class="mt-12 grid gap-6 md:grid-cols-3">
			{#each quotes as t (t.name)}
				<figure class="flex flex-col rounded-2xl border border-slatey-100 bg-slatey-50 p-6">
					<div class="flex gap-1 text-accent-500" aria-hidden="true">
						{#each Array(5) as _, i (i)}
							<svg class="h-4 w-4" viewBox="0 0 20 20" fill="currentColor">
								<path
									d="M10 1.5l2.6 5.3 5.9.9-4.3 4.1 1 5.8L10 15.9 4.8 18.6l1-5.8L1.5 8.7l5.9-.9L10 1.5z"
								/>
							</svg>
						{/each}
					</div>
					<blockquote class="mt-4 flex-1 text-ink-900/80">"{t.quote}"</blockquote>
					<figcaption class="mt-6 flex items-center gap-3">
						<span
							class="grid h-9 w-9 place-items-center rounded-full bg-accent-500/12 text-sm font-bold text-accent-700"
						>
							{t.name
								.split(' ')
								.map((p) => p[0])
								.join('')}
						</span>
						<span class="text-sm">
							<span class="block font-semibold text-ink-900">{t.name}</span>
							<span class="block text-ink-900/55">{t.role}</span>
						</span>
					</figcaption>
				</figure>
			{/each}
		</div>
	</div>
</section>
