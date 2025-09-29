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
		<div class="max-w-md mx-auto rounded-xl shadow-lg p-8 text-center backdrop-blur-sm content-card bg-white/90 dark:bg-slate-800/90 border border-white/20 dark:border-slate-700/50">
			<h1 class="text-4xl font-bold text-slate-900 dark:text-slate-100 mb-4 font-display">Hello Svelte 5!</h1>
			<p class="text-slate-600 dark:text-slate-300 mb-6 font-futura">Count: {count}</p>
			<button 
				onclick={whenBtnIsClicked}
				class="px-6 py-3 rounded-lg transition-colors bg-primary-500 hover:bg-primary-600 text-white mb-6"
			>
				<span class="font-futura">Click me! ({count})</span>
			</button>
			
			<div class="space-y-2">
				<input 
					type="text" 
					bind:value={randomTextType}
					class="w-full px-4 py-2 border border-slate-300 dark:border-slate-600 rounded-lg bg-white dark:bg-slate-700 text-slate-900 dark:text-slate-100 focus:outline-none focus:ring-2 focus:ring-primary-500 focus:border-transparent"
					placeholder="Type something..."
				/>
				<p class="text-slate-600 dark:text-slate-300 font-futura">{randomTextType}</p>
			</div>
		</div>
	</main>
	
	<Footer />
</div>
