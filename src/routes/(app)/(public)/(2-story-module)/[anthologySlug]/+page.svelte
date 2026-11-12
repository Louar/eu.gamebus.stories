<script lang="ts">
	import { resolve } from '$app/paths';
	import { AnthologyVisualization } from '$lib/db/schemas/2-story-module';
	import ArrowLeftIcon from '@lucide/svelte/icons/arrow-left';
	import AnthologyFeed from './AnthologyFeed.svelte';
	import AnthologyGrid from './AnthologyGrid.svelte';
	import type { PageData } from './$types';

	let { data }: { data: PageData } = $props();
</script>

{#if data.anthology.visualization === AnthologyVisualization.feed}
	<AnthologyFeed {data} />
	<a
		href={resolve('/')}
		class="fixed top-4 left-20 z-50 inline-flex size-12 items-center justify-center rounded-full bg-black/45 text-white shadow-sm backdrop-blur transition hover:bg-black/60 focus-visible:ring-2 focus-visible:ring-white focus-visible:outline-hidden"
		aria-label="Back to home"
	>
		<ArrowLeftIcon class="size-6" />
	</a>
{:else}
	<AnthologyGrid {data} />
{/if}
