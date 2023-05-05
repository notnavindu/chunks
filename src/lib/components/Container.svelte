<script lang="ts">
	export let pageId: string;
</script>

<main class="w-full h-screen relative">
	<div class="fixed top-5 left-5">Web Chunks</div>
	<div class="fixed top-5 right-5">{pageId}</div>
	<slot />
</main>
