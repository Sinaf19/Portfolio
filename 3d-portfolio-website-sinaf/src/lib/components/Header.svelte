<script lang="ts">
	import { type Content, isFilled } from '@prismicio/client';
	import NavBarLink from '$lib/components/NavBarLink.svelte';
	import Button from '$lib/components/Button.svelte';
	import IconMenu from '~icons/ic/twotone-menu';
	import IconClose from '~icons/ic/twotone-close';

	export let settings: Content.SettingsDocument;

	let open = false;

	function onLinkClick() {
		open = false;
	}
</script>

<header class="top-0 z-50 mx-auto max-w-7xl md:sticky md:top-4 relative">
	<nav>
		<div
			class="flex flex-col justify-between rounded-b-lg bg-slate-50 px-4 py-2 md:m4 md:flex-row md:items-center md:rounded-xl"
		>
			<div class="flex items-center justify-between">
				<a
					href="/"
					aria-label="Homepage"
					class="text-xl font-extrabold tracking-tighter text-slate-900"
				>
					{settings.data.name}
				</a>
				<button
					class="block p-2 text-2xl text-slate-800 md:hidden"
					aria-expanded={open}
					aria-label="Open Menu"
					on:click={() => (open = true)}
				>
					<IconMenu />
				</button>
			</div>
			<!-- Mobile Nav -->
			<ul
				class={`fixed inset-0 z-50 flex flex-col items-end gap-4 bg-slate-50 pr-4 pt-14 transition-transform duration-300 ease-in-out md:hidden ${open ? 'translate-x-0' : 'translate-x-[100%]'}`}
			>
				<li>
					<button
						class="fixed right-4 top-3 block p-2 text-2xl text-slate-800 md:hidden"
						aria-expanded={open}
						aria-label="Close Menu"
						on:click={() => (open = false)}
					>
						<IconClose />
					</button>
				</li>
				{#each settings.data.nav_items as { link, link_label }}
					<li>
						<NavBarLink field={link} label={link_label} type="mobile" {onLinkClick} />
					</li>
				{/each}
				{#if isFilled.link(settings.data.cta_link)}
					<Button
						linkField={settings.data.cta_link}
						label={settings.data.cta_label}
						showIcon={true}
					/>
				{/if}
			</ul>
			<!-- Desktop Nav -->
			<ul class="relative z-50 hidden flex-row items-center gap-1 bg-transparent py-0 md:flex">
				{#each settings.data.nav_items as { link, link_label }}
					<li>
						<NavBarLink field={link} label={link_label} type="desktop" {onLinkClick} />
					</li>
				{/each}

				{#if isFilled.link(settings.data.cta_link)}
					<Button
						linkField={settings.data.cta_link}
						label={settings.data.cta_label}
						class="ml-3"
						showIcon={true}
					/>
				{/if}
			</ul>
		</div>
	</nav>
</header>
