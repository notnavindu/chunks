<script lang="ts">
	import Container from '$components/Container.svelte';
	import { NEXT_TEXT } from '$lib/constants/001';
	import Icon from '@iconify/svelte';
	import delay from 'delay';
	import { onDestroy } from 'svelte';

	const rows = 5;
	const cols = 19;

	let active: string[] = [];
	let activeBright: string[] = [];
	let hovering = false;
	let loop: number;

	const getRandomNum = (max: number) => {
		return Math.floor(Math.random() * max);
	};
	const getRandomNode = () => {
		return `${getRandomNum(rows)}-${getRandomNum(cols)}`;
	};

	const shuffle = async () => {
		return new Promise<void>(async (resolve, reject) => {
			for (let i = 0; i <= 5; i++) {
				activeBright = [...activeBright, active[getRandomNum(9)]];

				await delay(20);
			}

			active = [];

			for (let i = 0; i <= 10; i++) {
				active = [...active, getRandomNode()];

				await delay(20);
			}

			resolve();
		});
	};

	const showText = async () => {
		for (let i = 0; i <= NEXT_TEXT.length; i++) {
			if (hovering) activeBright = [...activeBright, NEXT_TEXT[i]];

			await delay(15);
		}
	};

	onDestroy(() => {
		clearInterval(loop);
	});

	$: {
		hovering;
		if (hovering) {
			clearInterval(loop);
			active = [];
			activeBright = [];

			showText();
		} else {
			activeBright = [];
			shuffle();

			loop = setInterval(async () => {
				activeBright = [];
				await shuffle();
			}, 1100);
		}
	}
</script>

<Container
	pageId="001"
	inspirations={[
		'https://twitter.com/raunofreiberg/status/1648828609996509185',
		'https://nextjs.org/'
	]}
>
	<div class="w-full h-screen flex items-center justify-center p-4">
		<div
			class="w-full max-w-fit bg-gradient-to-br from-zinc-800/75 to-zinc-800/40 border border-zinc-800 rounded-xl p-5
            flex flex-col gap-3 sm:gap-6 overflow-hidden group cursor-pointer"
			on:mouseenter={() => (hovering = true)}
			on:mouseleave={() => (hovering = false)}
		>
			{#each { length: rows } as _, rowId}
				<div class="min-w-full w-fit flex flex-shrink-0 justify-between gap-1 sm:gap-5">
					{#each { length: cols } as __, colId}
						<div
							class="bg-zinc-600 h-[2px] w-[2px] rounded-full transition-all duration-500 transform"
							class:glow-light={active.includes(`${rowId}-${colId}`)}
							class:glow-bright={activeBright.includes(`${rowId}-${colId}`)}
						/>
					{/each}
				</div>
			{/each}
			<div>
				<div class="text-lg sm:text-xl mb-1 opacity-80 font-bold">Next.js 13</div>
				<div class="flex justify-between w-full items-end">
					<div class="w-full max-w-[250px] opacity-80 text-sm sm:text-base">
						The power of full-stack to the frontend. Read the release notes.
					</div>

					<div
						class="bg-white/10 group-hover:bg-white/[0.15] transition-all duration-300 p-2 rounded-full"
					>
						<Icon icon="material-symbols:arrow-right-alt" />
					</div>
				</div>
			</div>
		</div>
	</div>
</Container>

<style lang="postcss">
	.glow-light {
		background: #357fbf;
		box-shadow: 0px 0px 11px 3px #3b83f64b;
	}

	.glow-bright {
		background: #5cb2fd;
		box-shadow: 0px 0px 4px 3px #3b83f662;
		transform: scale(1.2);
	}
</style>
