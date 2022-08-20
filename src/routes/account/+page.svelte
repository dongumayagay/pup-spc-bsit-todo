<script>
	import { user } from '../../lib/stores';
	import { signOut } from 'firebase/auth';
	import { auth, db } from '$lib/firebaseClient';
	import {
		collection,
		addDoc,
		query,
		where,
		onSnapshot,
		doc,
		deleteDoc,
		updateDoc
	} from 'firebase/firestore';

	let listOfTodos = [];

	const todoCollection = collection(db, 'todos');
	const q = query(todoCollection, where('owner', '==', $user.uid));

	const unsubscribe = onSnapshot(q, (querySnapshot) => {
		const todos = [];
		querySnapshot.forEach((doc) => {
			todos.push({ ...doc.data(), id: doc.id });
		});
		listOfTodos = [...todos];
		console.log(listOfTodos);
	});

	async function addTodo() {
		const text = prompt('add todo');
		if (text == null || text == '') return;

		await addDoc(todoCollection, {
			text: text,
			owner: $user.uid
		});
	}

	async function logout() {
		await signOut(auth);
	}

	async function deleteTodo(id) {
		await deleteDoc(doc(db, 'todos', id));
	}

	async function updateTodo(id, text) {
		await updateDoc(doc(db, 'todos', id), {
			text: text
		});
	}
</script>

<main class="h-screen grid place-items-center text-white">
	{#if $user != null}
		<div class="flex flex-col gap-4">
			<h1 class="text-2xl">Hi {$user.email}</h1>
			<button class="bg-black text-white px-3 py-2" on:click={logout}>logout</button>
			<button on:click={addTodo} class=" bg-indigo-500 py-2">add todo</button>
			<ul class=" py-4 flex flex-col gap-4">
				{#each listOfTodos as item}
					<li class="text-black">
						<input class=" p-1" type="text" bind:value={item.text} />
						<button
							on:click={() => {
								updateTodo(item.id, item.text);
							}}
							class="bg-green-500 text-white p-1">update</button
						>
						<button
							on:click={() => {
								deleteTodo(item.id);
							}}
							class="bg-red-500 text-white p-1">delete</button
						>
					</li>
				{/each}
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
