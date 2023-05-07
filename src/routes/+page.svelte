<script>
	import { chunks } from '$lib/constants';
</script>

<main class="w-full min-h-screen grid grid-cols-1 sm:grid-cols-2">
	<div class="h-fit sm:h-screen p-5 sm:p-12 flex flex-col">
		<div class="font-light max-h-screen text-4xl sm:text-6xl lg:text-9xl">Chunks</div>
		<div class="font-thin pl-1 sm:pl-2 lg:pl-4 text-sm sm:text-base lg:text-2xl opacity-75">
			by navindu
		</div>

		<div class="text-xs mt-8 sm:mt-auto flex gap-3 pl-1 sm:pl-2 lg:pl-4">
			<div>GITHUB</div>
			<div>PORTFOLIO</div>
			<div>TWITTER</div>
		</div>
	</div>

	<div class="max-h-fit sm:max-h-screen overflow-scroll p-5 sm:p-12 flex flex-col gap-3">
		{#each chunks as chunk}
			<a href={chunk.id} class="w-full self-center">
				<div class="text-base sm:text-lg lg:text-2xl grid grid-cols-5">
					<div>{chunk.id}</div>
					<div class="opacity-70 col-span-3">{chunk.title}</div>
					<div class="justify-self-end">↗</div>
				</div>
			</a>
		{/each}

		<div class="mt-12 sm:mt-auto text-base sm:text-xl opacity-75 font-thin">
			Hey there! <br /><br /> I just made this site and there's not much to see here <u>yet</u>.

			<br />
			<br />
			I will keep updating Chunks with cool ui experiments as much as I can. So, be a little ★ and give
			<a class="underline underline-offset-2" href="https://github.com/notnavindu/web-chunks">
				this repo
			</a> a ★
		</div>
	</div>
</main>
