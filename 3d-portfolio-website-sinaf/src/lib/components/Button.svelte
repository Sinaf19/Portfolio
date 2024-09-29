<script lang="ts">
	import type { KeyTextField, LinkField } from '@prismicio/client';
	import { PrismicLink } from '@prismicio/svelte';
	import IconArrow from '~icons/ic/outline-arrow-outward';

	export let linkField: LinkField;
	export let label: KeyTextField;
	export let showIcon: true;
	let className: string = '';
	export { className as class };
</script>

<PrismicLink
	field={linkField}
	class={`group relative flex w-fit items-center justify-center overflow-hidden rounded-md border-2 border-slate-900 bg-slate-50 px-4 py-2 font-bold transition-transform ease-in-out hover:scale-105 ${className}`}
>
	<span
		class={`absolute inset-0 z-0 h-full rounded bg-yellow-300 transition-transform duration-300 ease-in-out group-hover:translate-y-0 translate-y-9`}
	></span>

	<span class="relative flex items-center justify-center gap-2">
		{label}
	</span>

	{#if showIcon}
		<span class="relative flex items-center justify-center gap-2 ml-1.5">
			<IconArrow />
		</span>
	{/if}
</PrismicLink>
