<!-- src/routes/+page.svelte -->
<script lang="ts">
	import Nav from '$lib/components/Nav.svelte';
	import Hero from '$lib/components/Hero.svelte';
	import LogoStrip from '$lib/components/LogoStrip.svelte';
	import FeatureShowcase from '$lib/components/FeatureShowcase.svelte';
	import PricingTable from '$lib/components/PricingTable.svelte';
	import Testimonials from '$lib/components/Testimonials.svelte';
	import DemoForm from '$lib/components/DemoForm.svelte';
	import Footer from '$lib/components/Footer.svelte';

	const title = "Flowbase — Project management that respects your team's time";
	const description =
		'Flowbase plans the work, balances the load, and keeps small teams in sync so you ship on schedule without burning out.';
</script>

<svelte:head>
	<title>{title}</title>
	<meta name="description" content={description} />
	<meta property="og:title" content={title} />
	<meta property="og:description" content={description} />
	<meta property="og:type" content="website" />
	<meta name="twitter:card" content="summary_large_image" />
</svelte:head>

<Nav />

<main>
	<Hero />
	<LogoStrip />
	<FeatureShowcase />
	<PricingTable />
	<Testimonials />
	<DemoForm />
</main>

<Footer />
