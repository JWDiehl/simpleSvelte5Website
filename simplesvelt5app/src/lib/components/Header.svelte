<script>
	let { title } = $props();
	let searchQuery = $state('');

	const handleSearch = () => {
		if (searchQuery.trim()) {
			// Use Google search
			const searchUrl = `https://www.google.com/search?q=${encodeURIComponent(searchQuery.trim())}`;
			window.open(searchUrl, '_blank', 'noopener,noreferrer');
		}
	};

	const handleKeyPress = (event) => {
		if (event.key === 'Enter') {
			handleSearch();
		}
	};
</script>

<header class="shadow-sm border-b" style="background-color: transparent !important; backdrop-filter: blur(3px);">
	<div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
		<div class="flex flex-col space-y-4 py-6">
			<!-- Top row: Title and Navigation -->
			<div class="flex justify-between items-center">
				<div class="flex items-center">
					<h1 class="text-2xl font-bold text-gray-900">{title}</h1>
				</div>
				<nav class="hidden md:flex space-x-8">
					<a href="/" class="text-gray-500 hover:text-gray-900 transition-colors">Home</a>
					<a href="/about" class="text-gray-500 hover:text-gray-900 transition-colors">About</a>
					<a href="/contact" class="text-gray-500 hover:text-gray-900 transition-colors">Contact</a>
				</nav>
			</div>
			
			<!-- Search Bar - Always visible -->
			<div class="flex justify-center items-center space-x-8">
				<button
					onclick={handleSearch}
					class="bg-indigo-600 text-white px-6 py-2 rounded-lg hover:bg-indigo-700 transition-colors flex items-center space-x-2"
				>
					<svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
						<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M21 21l-6-6m2-5a7 7 0 11-14 0 7 7 0 0114 0z"></path>
					</svg>
					<span>Search</span>
				</button>
				<div class="w-1/4">
					<input
						type="text"
						bind:value={searchQuery}
						onkeypress={handleKeyPress}
						placeholder="Search Google..."
						class="w-full px-4 py-2 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-indigo-500 focus:border-transparent"
					/>
				</div>
			</div>
		</div>
	</div>
</header>
