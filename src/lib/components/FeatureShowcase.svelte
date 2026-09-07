<!-- src/lib/components/FeatureShowcase.svelte -->
<script lang="ts">
	import { fade, fly } from 'svelte/transition';
	import features from '$lib/data/features.json';
	import Icon from './Icon.svelte';

	let activeId = $state(features[0].id);
	const active = $derived(features.find((f) => f.id === activeId) ?? features[0]);
</script>

<section id="features" class="bg-white py-20 sm:py-28">
	<div class="container-page">
		<div class="max-w-2xl">
			<span class="text-sm font-semibold tracking-wide text-accent-600 uppercase">Features</span>
			<h2 class="mt-3 text-3xl font-extrabold tracking-tight text-ink-900 sm:text-4xl">
				Everything a small team needs to stay on track
			</h2>
			<p class="mt-4 text-lg text-ink-900/60">
				Pick a capability to see how it works. No add-ons, no per-feature upsells.
			</p>
		</div>

		<div class="mt-12 grid gap-6 lg:grid-cols-[22rem_1fr] lg:gap-10">
			<!-- Tab list -->
			<div role="tablist" aria-label="Product features" class="flex flex-col gap-2">
				{#each features as feature (feature.id)}
					<button
						role="tab"
						id="tab-{feature.id}"
						aria-selected={activeId === feature.id}
						aria-controls="panel-{feature.id}"
						class="group flex items-start gap-4 rounded-xl border p-4 text-left transition-colors"
						class:border-accent-500={activeId === feature.id}
						class:bg-slatey-50={activeId === feature.id}
						class:border-slatey-100={activeId !== feature.id}
						class:hover:border-slatey-100={activeId !== feature.id}
						onclick={() => (activeId = feature.id)}
					>
						<span
							class="mt-0.5 grid h-10 w-10 shrink-0 place-items-center rounded-lg transition-colors"
							class:bg-accent-500={activeId === feature.id}
							class:text-white={activeId === feature.id}
							class:bg-slatey-100={activeId !== feature.id}
							class:text-ink-900={activeId !== feature.id}
						>
							<Icon name={feature.icon} class="h-5 w-5" />
						</span>
						<span>
							<span class="block font-semibold text-ink-900">{feature.title}</span>
							<span class="mt-1 block text-sm text-ink-900/55">{feature.shortDescription}</span>
						</span>
					</button>
				{/each}
			</div>

			<!-- Detail panel -->
			<div
				class="relative grid overflow-hidden rounded-2xl bg-ink-950 p-6 sm:p-10 [&>*]:[grid-area:1/1]"
			>
				{#key active.id}
					<div
						class="flex flex-col"
						in:fly={{ y: 12, duration: 320, delay: 90 }}
						out:fade={{ duration: 90 }}
					>
						<span class="grid h-12 w-12 place-items-center rounded-xl bg-accent-500 text-white">
							<Icon name={active.icon} class="h-6 w-6" />
						</span>
						<h3 class="mt-5 text-2xl font-bold text-white">{active.title}</h3>
						<p class="mt-3 max-w-xl text-white/70">{active.detail}</p>

						<div class="mt-8">
							<div class="rounded-xl border border-white/10 bg-ink-900 p-4">
								<div class="flex items-center gap-2">
									<span class="h-2 w-2 rounded-full bg-accent-400"></span>
									<span class="text-xs font-medium text-white/50">{active.title} · live</span>
								</div>
								<div class="mt-3 grid grid-cols-3 gap-2">
									{#each [70, 45, 88] as w, i (i)}
										<div class="rounded-lg bg-white/5 p-3">
											<div class="h-1.5 overflow-hidden rounded-full bg-white/10">
												<div class="h-full rounded-full bg-accent-500" style="width:{w}%"></div>
											</div>
											<div class="mt-2 h-1.5 w-2/3 rounded-full bg-white/10"></div>
										</div>
									{/each}
								</div>
							</div>
						</div>
					</div>
				{/key}
			</div>
		</div>
	</div>
</section>
