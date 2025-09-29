<script>
	import Header from '$lib/components/Header.svelte';
	import Footer from '$lib/components/Footer.svelte';
	
	let count = $state(0);
	let b = 4;
    let randomTextType = $state("");

	// function to increment the count
	const whenBtnIsClicked = (a) => {
		count += 1;
	};
</script>


<div class="min-h-screen flex flex-col">
	<Header title="Svelte 5 Counter App" />
	
	<main class="flex-grow flex items-center justify-center">
		<div class="max-w-md mx-auto bg-white bg-opacity-90 rounded-xl shadow-lg p-8 text-center backdrop-blur-sm">
			<h1 class="text-4xl font-bold text-gray-800 mb-4">Hello Svelte 5!</h1>
			<p class="text-gray-600 mb-6">Count: {count}</p>
			<button 
				onclick={whenBtnIsClicked}
				class="bg-indigo-600 text-white px-6 py-3 rounded-lg hover:bg-indigo-700 transition-colors"
			>
				Click me! ({count})
			</button>

            <input type="text" bind:value={randomTextType} />

            <p>{randomTextType}</p>
		</div>
	</main>
	
	<Footer />
</div>
