<script lang="ts">
	export let pageId: string;
	export let inspirationLink: string;
</script>

<main class="w-full h-screen relative">
	<div class="fixed top-5 left-5">Web Chunks</div>
	<div class="fixed top-5 right-5">{pageId}</div>
	<slot />
	<div class="fixed bottom-5 left-5 text-xs opacity-50">
		<a href="https://github.com/notnavindu/web-chunks"> Code </a>
	</div>
	<div class="fixed bottom-5 right-5 text-xs opacity-50">
		<a href={inspirationLink}> Inspiration </a>
	</div>
</main>
