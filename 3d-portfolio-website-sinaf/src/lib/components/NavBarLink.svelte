<script lang="ts">
	import { asLink, type KeyTextField, type LinkField } from '@prismicio/client';
	import { page } from '$app/stores';
	import { PrismicLink } from '@prismicio/svelte';

	export let field: LinkField;
	export let label: KeyTextField;
	export let onLinkClick: (event: MouseEvent) => void;
	export let type: 'desktop' | 'mobile';

	// check if there is a path and if that includes our path
	const path = asLink(field);
	$: isActive = path && $page.url.pathname.includes(path);
</script>

{#if type === 'desktop'}
	<PrismicLink
			class="group relative block overflow-hidden rounded px-3 py-1 text-base font-bold text-slate-900"
			{field}
			on:click={onLinkClick}
			aria-current={isActive ? 'page' : undefined}
	>
		<span
				class={`absolute inset-0 z-0 h-full rounded bg-yellow-300 transition-transform duration-300 ease-in-out group-hover:translate-y-0 ${isActive ? 'translate-y-6' : 'translate-y-8'}`}
		></span>

		<span class="relative">
			{label}
		</span>
	</PrismicLink>
{:else}
	<PrismicLink
			class="group relative block overflow-hidden rounded px-3 text-3xl font-bold text-slate-900"
			{field}
			on:click={onLinkClick}
			aria-current={isActive ? 'page' : undefined}
	>
		<span
				class={`absolute inset-0 z-0 h-full rounded bg-yellow-300 transition-transform duration-300 ease-in-out group-hover:translate-y-0 ${isActive ? 'translate-y-6' : 'translate-y-16'}`}
		></span>

		<span class="relative">
			{label}
		</span>
	</PrismicLink>
{/if}
