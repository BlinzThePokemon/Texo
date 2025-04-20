<script lang="ts">
	import Topbar from '$lib/components/Topbar.svelte';
	import Footer from '$lib/components/Footer.svelte';
	import Joinroom from '$lib/components/Joinroom.svelte';
	import Createroom from '$lib/components/Createroom.svelte';
	import Joinrandomroom from '$lib/components/Joinrandomroom.svelte';
</script>

<main>
	<Topbar />
	<div class="flex flex-col items-center justify-center">
		<h1 class="mt-8 select-none text-4xl font-bold text-white underline-offset-4 hover:underline">
			Welcome to Texo
		</h1>
		<p class="mt-4 text-2xl text-gray-400">
			Seems like you are not in a room. Join or create your own room to chat with others!
		</p>

		<span class="select-none text-white">
			<Createroom />
			<Joinroom />
		</span>

		<div class="-mt-2 select-none text-white">
			<Joinrandomroom />
		</div>

		<div class="text-display mt-8 h-[50rem] w-[50rem] rounded-lg bg-[--bg-3] ring-black"></div>
	</div>
</main>

<style>
	main {
		height: auto;
		padding-bottom: 10rem;
		width: auto;
		background-color: var(--bg-1);
		background-image: radial-gradient(rgb(49, 49, 49) 1px, transparent 0);
		background-size: 40px 40px;
	}

	::selection {
		background-color: var(--bg-4);
		color: white;
	}

	.text-display {
		box-shadow: 5px 5px 5px black;
	}
</style>
