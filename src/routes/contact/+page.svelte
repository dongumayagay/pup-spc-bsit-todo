<script>
	let showModal = false;

	function openModal() {
		showModal = true;
	}

	function closeModal() {
		showModal = false;
	}
</script>

<main class="h-screen grid place-items-center">
	<div class="text-white">
		<h1>contact</h1>
		<button on:click={openModal} class=" bg-black text-white py-2 px-3">open modal</button>
	</div>
</main>

{#if showModal == true}
	<div on:click|self={closeModal} class="fixed inset-0 bg-black/50 grid place-items-center">
		<main class=" p-4 flex justify-between items-start w-[512px] h-[512px] bg-white">
			pop
			<button on:click={closeModal} class=" bg-red-500"> close </button>
		</main>
	</div>
{/if}
