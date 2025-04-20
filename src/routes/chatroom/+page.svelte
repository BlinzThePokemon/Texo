<script lang="ts">
	import Topbar from '$lib/components/Topbar.svelte';
	import Footer from '$lib/components/Footer.svelte';
	import { database } from '$lib/firebase.js';
	import { ref, get, set } from 'firebase/database';
	import { onMount } from 'svelte';

	let roomId;

	onMount(() => {
		const params = new URLSearchParams(window.location.search);
		roomId = params.get('r');
		console.log('Room ID:', roomId);
		get(ref(database, 'rooms/' + roomId))
			.then((snapshot) => {
				if (snapshot.exists()) {
					const data = snapshot.val();

					const roomNumber = data.roomNumber;
					const roomName = data.roomName;
					const maxPeople = data.maxPeople;
					let messages = data.messages;
					const roomTopic = data.roomTopic;
				} else {
					console.log('Room does not exist');
				}
			})
			.catch((error) => {
				console.error('Error getting room data:', error);
			});
	});
</script>

<main>
	<Topbar />
	<div class="flex flex-col items-center justify-center">
		<h1 class="mt-4 select-none text-4xl font-bold text-white underline-offset-4 hover:underline">
			Chat Room
		</h1>
		<p class="mt-4 text-2xl text-gray-400">Chat with people about various topics and enjoy!</p>
		<div class="chat-box mt-5 flex h-[50rem] w-[50rem] bg-[--bg-3]">
			<div class="h-[50rem] w-[25rem]"></div>
			<div class="h-[50rem] w-[25rem]"></div>
		</div>
		<input
			type="text"
			placeholder="Type your message here..."
			class="message w-[49.5rem] mr-3 h-16 bg-[--bg-3] text-white p-4 text-lg"
		/>
	</div>
	<Footer />
</main>

<style>
	main {
		height: auto;
		padding-bottom: 15rem;
		width: auto;
		background-color: var(--bg-1);
		background-image: radial-gradient(rgb(49, 49, 49) 1px, transparent 0);
		background-size: 40px 40px;
	}

	.chat-box {
		overflow-y: scroll;
		border-top-left-radius: 0.5rem;
		border-top-right-radius: 0.5rem;
	}

	::selection {
		background-color: var(--bg-5);
		color: white;
	}

	.message {
		left: 50%;
		border-bottom-left-radius: 0.5rem;
		border-bottom-right-radius: 0.5rem;
		outline: none;
		border-top: 1px solid rgb(85, 85, 85);
		border-left: none;
		border-right: none;
		border-bottom: none;
		font-family: 'Poppins', sans-serif;
	}

	.message:focus {
		outline: none;
	}

	input::placeholder {
		user-select: none;
		border: none;
		outline: none;
	}
</style>
