<script>
	import { user } from '$lib/stores.js';
	import { goto } from '$app/navigation';
	let email = '';
	let password = '';

	function submitHandler() {
		$user = {
			email
		};
		goto('/account');
	}
</script>

<main class="h-screen grid place-items-center">
	<form
		on:submit|preventDefault={submitHandler}
		class="text-white flex flex-col gap-4 w-[512px] mx-auto text-center"
	>
		<h1 class=" text-2xl">SIGN IN</h1>
		<input
			class="bg-white/30 px-3 py-1 rounded placeholder:text-white"
			type="email"
			name=""
			id=""
			placeholder="Email"
			bind:value={email}
		/>
		<input
			class="bg-white/30 px-3 py-1 rounded placeholder:text-white"
			type="password"
			name=""
			id=""
			placeholder="Password"
			bind:value={password}
		/>
		<button class=" bg-black py-2 rounded" type="submit">LOGIN</button>
	</form>
</main>
