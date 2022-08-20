<script>
	import '../app.postcss';
	import { auth } from '$lib/firebaseClient.js';
	import { onAuthStateChanged } from 'firebase/auth';
	import { user } from '$lib/stores';
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
	<nav class="fixed w-full flex justify-evenly text-white upper">
		<a class="" href="/">Homepage</a>
		<a class="" href="/about">About page</a>
		<a class="" href="/contact">contact page</a>
		<a href="/account">account</a>
	</nav>
	<slot />
</main>
