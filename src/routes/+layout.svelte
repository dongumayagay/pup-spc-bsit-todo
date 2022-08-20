<script>
	import '../app.postcss';
	import { auth } from '$lib/firebaseClient.js';
	import { onAuthStateChanged } from 'firebase/auth';
	import { user } from '$lib/stores';
	import Navbar from '$lib/components/Navbar.svelte';

	onAuthStateChanged(auth, (fb_user) => {
		if (fb_user) {
			$user = fb_user;
			console.log(fb_user);
		} else {
			$user = null;
		}
	});
</script>

<main class=" bg-gradient-to-br from-indigo-500 via-pink-500 to-blue-500 ">
	<Navbar />
	<slot />
</main>
