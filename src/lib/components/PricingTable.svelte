<!-- src/lib/components/PricingTable.svelte -->
<script lang="ts">
	import tiers from '$lib/data/pricingTiers.json';
	import Icon from './Icon.svelte';

	let annual = $state(true);
</script>

<section id="pricing" class="bg-slatey-50 py-20 sm:py-28">
	<div class="container-page">
		<div class="mx-auto max-w-2xl text-center">
			<span class="text-sm font-semibold tracking-wide text-accent-600 uppercase">Pricing</span>
			<h2 class="mt-3 text-3xl font-extrabold tracking-tight text-ink-900 sm:text-4xl">
				Simple pricing that scales with your team
			</h2>
			<p class="mt-4 text-lg text-ink-900/60">Per user, per month. Switch or cancel anytime.</p>
		</div>

		<!-- Billing toggle -->
		<div class="mt-8 flex items-center justify-center gap-4">
			<span class="text-sm font-medium {annual ? 'text-ink-900/45' : 'text-ink-900'}">Monthly</span>
			<button
				type="button"
				role="switch"
				aria-checked={annual}
				aria-label="Toggle annual billing"
				onclick={() => (annual = !annual)}
				class="relative h-7 w-12 rounded-full transition-colors {annual
					? 'bg-accent-500'
					: 'bg-ink-900'}"
			>
				<span
					class="absolute top-1 left-1 h-5 w-5 rounded-full bg-white transition-transform duration-200 {annual
						? 'translate-x-5'
						: ''}"
				></span>
			</button>
			<span class="flex items-center gap-2 text-sm font-medium {annual ? 'text-ink-900' : 'text-ink-900/45'}">
				Annual
				<span class="rounded-full bg-accent-500/12 px-2 py-0.5 text-xs font-semibold text-accent-700">
					Save ~17%
				</span>
			</span>
		</div>

		<div class="mt-12 grid gap-6 lg:grid-cols-3">
			{#each tiers as tier (tier.name)}
				<div
					class="relative flex flex-col rounded-2xl border bg-white p-7 {tier.featured
						? 'border-accent-500 shadow-xl shadow-accent-700/10'
						: 'border-slatey-100'}"
				>
					{#if tier.featured}
						<span
							class="absolute -top-3 left-7 rounded-full bg-accent-500 px-3 py-1 text-xs font-semibold text-white"
							>Most popular</span
						>
					{/if}

					<h3 class="text-lg font-bold text-ink-900">{tier.name}</h3>
					<p class="mt-1 text-sm text-ink-900/55">{tier.description}</p>

					<div class="mt-5 flex items-baseline gap-1">
						<span class="text-4xl font-extrabold tracking-tight text-ink-900">
							${annual ? tier.annualPrice : tier.monthlyPrice}
						</span>
						<span class="text-sm text-ink-900/50">/user/mo</span>
					</div>
					<p class="mt-1 h-4 text-xs text-ink-900/45">
						{annual ? `Billed annually ($${tier.annualPrice * 12}/user/yr)` : 'Billed monthly'}
					</p>

					<a
						href="#demo"
						class="mt-6 rounded-xl px-4 py-2.5 text-center text-sm font-semibold transition-colors {tier.featured
							? 'bg-accent-500 text-white hover:bg-accent-600'
							: 'bg-slatey-100 text-ink-900 hover:bg-slatey-50'}"
					>
						Get started
					</a>

					<ul class="mt-7 flex flex-col gap-3 border-t border-slatey-100 pt-6">
						{#each tier.features as feature (feature)}
							<li class="flex items-start gap-3 text-sm text-ink-900/75">
								<Icon name="check" class="mt-0.5 h-4 w-4 shrink-0 text-accent-600" />
								<span>{feature}</span>
							</li>
						{/each}
					</ul>
				</div>
			{/each}
		</div>
	</div>
</section>
