<script>
	import { user } from '../../lib/stores';
	import { signOut } from 'firebase/auth';
	import { auth } from '$lib/firebaseClient';
	async function logout() {
		await signOut(auth);
	}
</script>

<main class="h-screen grid place-items-center text-white">
	{#if $user != null}
		<div>
			<h1 class="text-2xl">Hi {$user.email}</h1>
			<button class="bg-black text-white px-3 py-2" on:click={logout}>logout</button>
		</div>
	{:else}
		<div class="flex flex-col gap-4 text-center">
			you are not login
			<a class="bg-black text-white px-3 py-2" href="/account/login">login</a>
			<a class="bg-black text-white px-3 py-2" href="/account/register">register</a>
		</div>
	{/if}
</main>
