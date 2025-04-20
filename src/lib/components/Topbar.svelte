<script lang="ts">
	import Createroom from './Createroom.svelte';
	import Search from './Search.svelte';
</script>

<div class="topbar sticky select-none bg-transparent backdrop-blur-sm">
	<nav class="flex w-full items-center px-4">
		<!-- Left section -->
		<div class="flex flex-1 justify-start text-white">
			<div class="flex items-center space-x-2">
				<img src="favicon.png" alt="Logo" class="h-10 w-10" />
				<button onclick={() => (window.location.href = '/')}
					><p class="text-1 text-3xl hover:underline" style="letter-spacing: 0.0px;">
						Texo
					</p></button
				>
			</div>
		</div>

		<!-- Center section -->
		<div class="flex flex-1 justify-center">
			<Search />
		</div>

		<!-- Right section -->
		<div class="flex flex-1 justify-end">
			<div class="flex items-center space-x-2 text-white">
				<!-- Create Room -->
				<Createroom />

				<!-- GitHub Button with Tooltip -->
				<div class="group relative">
					<button
						aria-label="Github"
						class="rounded-md px-2 py-2 transition-all delay-100 duration-100 hover:bg-[--bg-4] focus:bg-[--bg-4]"
					>
						<i class="icon fa-brands fa-github fa-xl" style="color: #ffffff;"></i>
					</button>
					<span
						class="absolute left-1/2 top-full z-20 mt-1 -translate-x-1/2 scale-0 whitespace-nowrap rounded-md bg-black px-2 py-1 text-xs font-semibold text-white transition-transform group-hover:scale-100"
					>
						Github
					</span>
				</div>
				<!-- Settings Button with Tooltip -->
				<div class="group relative">
					<button
						aria-label="Settings"
						class="rounded-md px-2 py-2 transition-all delay-100 duration-100 hover:bg-[--bg-4] focus:bg-[--bg-4]"
					>
						<i class="icon fa-solid fa-gear fa-xl" style="color: #ffffff;"></i>
					</button>
					<span
						class="absolute left-1/2 top-full z-20 mt-1 -translate-x-1/2 scale-0 whitespace-nowrap rounded-md bg-black px-2 py-1 text-xs font-semibold text-white transition-transform group-hover:scale-100"
					>
						Settings
					</span>
				</div>
				<div class="group relative"></div>
			</div>
		</div>
	</nav>
</div>

<style>
	.icon {
		transition: all 0.8s;

		&:hover {
			transform: rotate(360deg);
		}
	}

	.topbar {
		height: 3.7rem;
		width: 100%;
		top: 0;
		left: 0;
		z-index: 10;
		box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
		border-bottom: 1px solid rgba(255, 255, 255, 0.1);
		transition: all 0.3s ease-in-out;
		display: flex;
	}
</style>