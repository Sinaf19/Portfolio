<script lang="ts">
	import type { Content } from '@prismicio/client';
	import Bounded from '$lib/components/Bounded.svelte';
	import Heading from '$lib/components/Heading.svelte';
	import {PrismicRichText} from "@prismicio/svelte";

	export let slice: Content.ExperienceSlice;
</script>

<Bounded data-slice-type={slice.slice_type} data-slice-variation={slice.variation}>
	<Heading size="lg" class="mb-8" tag="h2">
		{slice.primary.heading}
	</Heading>

	{#each slice.primary.items as { title, time_period, institution, description }}

<div>
	<Heading tag="h3" size="sm">
		{title}
	</Heading>
	<p class="mt-1 flex w-fit items-center gap-1 text-2xl font-semibold tracking-light text-slate-400">
		<span>{time_period}</span> {' '}
		<span class="text-3xl font-extralight ">/</span> {' '}
		<span>{institution}</span>
	</p>
	<div class="prose prose-lg prose-invert mt-4 mb-14">
		<PrismicRichText field={description}>

		</PrismicRichText>
	</div>
</div>

	{/each}
</Bounded>
