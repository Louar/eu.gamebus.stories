<script lang="ts">
	import { resolve } from '$app/paths';
	import Story from '$lib/components/app/player/Story.svelte';
	import ArrowLeftIcon from '@lucide/svelte/icons/arrow-left';
	import type { PageProps } from './$types';

	let { data, params }: PageProps = $props();
	let story = $derived(data.story);
	// svelte-ignore state_referenced_locally
	let players = $state(data.players);
</script>

<svelte:head>
	<title>{story.name}</title>
</svelte:head>

<Story {story} {players} />

<a
	href={resolve('/(app)/(public)/(2-story-module)/[anthologySlug]', {
		anthologySlug: params.anthologySlug
	})}
	class="fixed top-4 left-4 z-50 inline-flex size-12 items-center justify-center rounded-full bg-black/45 text-white shadow-sm backdrop-blur transition hover:bg-black/60 focus-visible:ring-2 focus-visible:ring-white focus-visible:outline-hidden"
	aria-label="Back to anthology"
>
	<ArrowLeftIcon class="size-6" />
</a>

<style lang="postcss">
	@reference 'tailwindcss';
	:global(body) {
		@apply bg-transparent;
	}
</style>
