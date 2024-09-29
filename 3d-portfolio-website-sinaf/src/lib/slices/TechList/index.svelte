<script lang="ts">
	import type { Content } from '@prismicio/client';
	import Bounded from '$lib/components/Bounded.svelte';
	import Heading from '$lib/components/Heading.svelte';

	export let slice: Content.TechListSlice;
</script>

<section
	data-slice-type={slice.slice_type}
	data-slice-variation={slice.variation}
	class="overflow-hidden"
>
	<Bounded as="div">
		<Heading size="xl" class="mb-8" tag="h2">
			{slice.primary.heading}
		</Heading>
	</Bounded>

	{#each slice.primary.items as item}
		{item.techcolor}
	{/each}
</section>
