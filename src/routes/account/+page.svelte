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
		<div class="flex flex-col gap-4">
			<h1 class="text-2xl">Hi {$user.email}</h1>
			<button class="bg-black text-white px-3 py-2" on:click={logout}>logout</button>
			<button class=" bg-indigo-500 py-2">add todo</button>
			<ul class=" py-4 flex flex-col gap-4">
				<li class="text-black">
					<input class=" p-1" type="text" value="text" />
					<button class="bg-green-500 text-white p-1">update</button>
					<button class="bg-red-500 text-white p-1">delete</button>
				</li>
				<li class="text-black">
					<input class=" p-1" type="text" value="text" />
					<button class="bg-green-500 text-white p-1">update</button>
					<button class="bg-red-500 text-white p-1">delete</button>
				</li>
				<li class="text-black">
					<input class=" p-1" type="text" value="text" />
					<button class="bg-green-500 text-white p-1">update</button>
					<button class="bg-red-500 text-white p-1">delete</button>
				</li>
			</ul>
		</div>
	{:else}
		<div class="flex flex-col gap-4 text-center">
			you are not login
			<a class="bg-black text-white px-3 py-2" href="/account/login">login</a>
			<a class="bg-black text-white px-3 py-2" href="/account/register">register</a>
		</div>
	{/if}
</main>
