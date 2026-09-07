<!-- src/lib/components/DemoForm.svelte -->
<script lang="ts">
	import { fade, fly } from 'svelte/transition';
	import Icon from './Icon.svelte';

	type Field = 'name' | 'email' | 'company' | 'teamSize';

	const teamSizes = ['1–5', '6–20', '21–50', '51–200', '200+'];

	let form = $state({ name: '', email: '', company: '', teamSize: '', message: '' });
	let touched = $state<Record<Field, boolean>>({
		name: false,
		email: false,
		company: false,
		teamSize: false
	});
	let submitted = $state(false);
	let done = $state(false);

	const emailOk = $derived(/^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(form.email.trim()));

	const errors = $derived({
		name: form.name.trim() ? '' : 'Please enter your name.',
		email: !form.email.trim()
			? 'Please enter your work email.'
			: emailOk
				? ''
				: 'Enter a valid email address.',
		company: form.company.trim() ? '' : 'Please enter your company.',
		teamSize: form.teamSize ? '' : 'Select a team size.'
	});

	const isValid = $derived(!errors.name && !errors.email && !errors.company && !errors.teamSize);

	function show(field: Field) {
		return (touched[field] || submitted) && errors[field];
	}

	function handleSubmit(event: SubmitEvent) {
		event.preventDefault();
		submitted = true;
		if (!isValid) {
			// focus first invalid field
			const order: Field[] = ['name', 'email', 'company', 'teamSize'];
			const first = order.find((f) => errors[f]);
			if (first) document.getElementById(`demo-${first}`)?.focus();
			return;
		}
		// Mock submission — no backend.
		done = true;
	}

	function reset() {
		form = { name: '', email: '', company: '', teamSize: '', message: '' };
		touched = { name: false, email: false, company: false, teamSize: false };
		submitted = false;
		done = false;
	}

	const inputBase =
		'w-full rounded-lg border bg-white px-3.5 py-2.5 text-sm text-ink-900 outline-none transition-colors placeholder:text-ink-900/35 focus:ring-2 focus:ring-accent-500/40';
</script>

<section id="demo" class="bg-ink-950 py-20 sm:py-28">
	<div class="container-page">
		<div class="grid gap-12 lg:grid-cols-2 lg:gap-16">
			<div class="max-w-md">
				<span class="text-sm font-semibold tracking-wide text-accent-400 uppercase">Get started</span>
				<h2 class="mt-3 text-3xl font-extrabold tracking-tight text-white sm:text-4xl">
					See Flowbase with your own workflow
				</h2>
				<p class="mt-4 text-lg text-white/65">
					Tell us a little about your team and we'll set up a 30-minute walkthrough tailored to how
					you work.
				</p>

				<ul class="mt-8 flex flex-col gap-4">
					{#each ['No sales pressure — a working session', 'Bring a real project and we will model it', 'Trial access activated the same day'] as point (point)}
						<li class="flex items-start gap-3 text-sm text-white/70">
							<Icon name="check" class="mt-0.5 h-4 w-4 shrink-0 text-accent-400" />
							<span>{point}</span>
						</li>
					{/each}
				</ul>
			</div>

			<div class="rounded-2xl bg-white p-6 sm:p-8">
				{#if done}
					<div
						class="flex min-h-[24rem] flex-col items-center justify-center text-center"
						in:fly={{ y: 12, duration: 300 }}
					>
						<span class="grid h-14 w-14 place-items-center rounded-full bg-accent-500/12 text-accent-600">
							<Icon name="check" class="h-7 w-7" />
						</span>
						<h3 class="mt-5 text-xl font-bold text-ink-900">Thanks, we'll be in touch</h3>
						<p class="mt-2 max-w-sm text-sm text-ink-900/60">
							A member of the team will email {form.email} within one business day to schedule your
							walkthrough.
						</p>
						<button
							type="button"
							onclick={reset}
							class="mt-6 text-sm font-semibold text-accent-600 hover:text-accent-700"
						>
							Submit another request
						</button>
					</div>
				{:else}
					<form class="flex flex-col gap-4" novalidate onsubmit={handleSubmit} in:fade={{ duration: 150 }}>
						<div>
							<label for="demo-name" class="mb-1.5 block text-sm font-medium text-ink-900">Name</label>
							<input
								id="demo-name"
								type="text"
								autocomplete="name"
								bind:value={form.name}
								onblur={() => (touched.name = true)}
								class="{inputBase} {show('name') ? 'border-red-400' : 'border-slatey-100 focus:border-accent-500'}"
								aria-invalid={show('name') ? 'true' : undefined}
								aria-describedby={show('name') ? 'err-name' : undefined}
							/>
							{#if show('name')}
								<p id="err-name" class="mt-1 text-xs text-red-500">{errors.name}</p>
							{/if}
						</div>

						<div>
							<label for="demo-email" class="mb-1.5 block text-sm font-medium text-ink-900"
								>Work email</label
							>
							<input
								id="demo-email"
								type="email"
								autocomplete="email"
								bind:value={form.email}
								onblur={() => (touched.email = true)}
								class="{inputBase} {show('email') ? 'border-red-400' : 'border-slatey-100 focus:border-accent-500'}"
								aria-invalid={show('email') ? 'true' : undefined}
								aria-describedby={show('email') ? 'err-email' : undefined}
							/>
							{#if show('email')}
								<p id="err-email" class="mt-1 text-xs text-red-500">{errors.email}</p>
							{/if}
						</div>

						<div>
							<label for="demo-company" class="mb-1.5 block text-sm font-medium text-ink-900"
								>Company</label
							>
							<input
								id="demo-company"
								type="text"
								autocomplete="organization"
								bind:value={form.company}
								onblur={() => (touched.company = true)}
								class="{inputBase} {show('company') ? 'border-red-400' : 'border-slatey-100 focus:border-accent-500'}"
								aria-invalid={show('company') ? 'true' : undefined}
								aria-describedby={show('company') ? 'err-company' : undefined}
							/>
							{#if show('company')}
								<p id="err-company" class="mt-1 text-xs text-red-500">{errors.company}</p>
							{/if}
						</div>

						<div>
							<label for="demo-teamSize" class="mb-1.5 block text-sm font-medium text-ink-900"
								>Team size</label
							>
							<select
								id="demo-teamSize"
								bind:value={form.teamSize}
								onblur={() => (touched.teamSize = true)}
								class="{inputBase} {show('teamSize') ? 'border-red-400' : 'border-slatey-100 focus:border-accent-500'}"
								aria-invalid={show('teamSize') ? 'true' : undefined}
								aria-describedby={show('teamSize') ? 'err-teamSize' : undefined}
							>
								<option value="" disabled>Select…</option>
								{#each teamSizes as size (size)}
									<option value={size}>{size} people</option>
								{/each}
							</select>
							{#if show('teamSize')}
								<p id="err-teamSize" class="mt-1 text-xs text-red-500">{errors.teamSize}</p>
							{/if}
						</div>

						<div>
							<label for="demo-message" class="mb-1.5 block text-sm font-medium text-ink-900">
								Message <span class="font-normal text-ink-900/40">(optional)</span>
							</label>
							<textarea
								id="demo-message"
								rows="3"
								bind:value={form.message}
								placeholder="Anything specific you'd like us to cover?"
								class="{inputBase} resize-none border-slatey-100 focus:border-accent-500"
							></textarea>
						</div>

						{#if submitted && !isValid}
							<p class="text-xs text-red-500">Please fix the highlighted fields above.</p>
						{/if}

						<button
							type="submit"
							class="mt-1 rounded-xl bg-accent-500 px-5 py-3 text-sm font-semibold text-white transition-colors hover:bg-accent-600"
						>
							Request a demo
						</button>
						<p class="text-center text-xs text-ink-900/45">
							This is a portfolio demo — no data is sent anywhere.
						</p>
					</form>
				{/if}
			</div>
		</div>
	</div>
</section>
