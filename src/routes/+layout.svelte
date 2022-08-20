<script>
	import '../app.postcss';
</script>

<main class=" bg-gradient-to-br from-indigo-500 via-pink-500 to-blue-500 ">
	<nav class="fixed w-full flex justify-evenly text-white upper">
		<a class="" href="/">Homepage</a>
		<a class="" href="/about">About page</a>
		<a class="" href="/contact">contact page</a>
		<a class="" href="/account/register">register page</a>
		<a class="" href="/account/login">login page</a>
	</nav>
	<slot />
</main>
