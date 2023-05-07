<script lang="ts">
	export let pageId: string;
	export let inspirations: string[];
</script>

<main class="w-full h-screen relative">
	<a href="/" class="fixed top-5 left-5">Chunks</a>
	<div class="fixed top-5 right-5">{pageId}</div>
	<slot />
	<div class="fixed bottom-5 left-5 text-xs opacity-50">
		<a href="https://github.com/notnavindu/web-chunks"> Code </a>
	</div>
	<div class="fixed bottom-5 right-5 text-xs opacity-50">
		{#if inspirations.length > 1}
			<span>
				Inspirations
				{#each inspirations as inspo, i}
					<a href={inspo}> ({i}) </a>
				{/each}
			</span>
		{:else}
			<a href={inspirations[0]}> Inspiration </a>
		{/if}
	</div>
</main>
