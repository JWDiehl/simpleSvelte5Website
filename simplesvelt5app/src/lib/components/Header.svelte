<script>
	let { title } = $props();
	let searchQuery = $state('');
	let isDarkMode = $state(false);

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
	
	const toggleTheme = () => {
		isDarkMode = !isDarkMode;
		if (isDarkMode) {
			document.documentElement.classList.add('dark');
		} else {
			document.documentElement.classList.remove('dark');
		}
	};
</script>

<header class="shadow-sm border-b" style="background-color: transparent !important; backdrop-filter: blur(3px);">
	<div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
		<div class="flex flex-col space-y-4 py-6">
			<!-- Top row: Title, Navigation, and Theme Toggle -->
			<div class="flex justify-between items-center">
				<div class="flex items-center">
					<h1 class="text-2xl font-bold text-slate-900 dark:text-slate-100 font-phillies">{title}</h1>
				</div>
				<div class="flex items-center space-x-4">
					<nav class="hidden md:flex space-x-8">
						<a href="/" class="text-slate-600 dark:text-slate-300 hover:text-slate-900 dark:hover:text-slate-100 transition-colors font-phillies">Home</a>
						<a href="/about" class="text-slate-600 dark:text-slate-300 hover:text-slate-900 dark:hover:text-slate-100 transition-colors font-phillies">About</a>
						<a href="/contact" class="text-slate-600 dark:text-slate-300 hover:text-slate-900 dark:hover:text-slate-100 transition-colors font-phillies">Contact</a>
					</nav>
					<!-- Theme Toggle Button -->
					<button
						onclick={toggleTheme}
						class="px-4 py-2 rounded-lg transition-colors flex items-center space-x-2"
						style="background: var(--theme-primary); color: white; box-shadow: 0 4px 15px rgba(232, 24, 40, 0.3);"
						title={isDarkMode ? 'Switch to Light Mode' : 'Switch to Dark Mode'}
					>
						{#if isDarkMode}
							<!-- Sun icon for light mode -->
							<svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
								<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 3v1m0 16v1m9-9h-1M4 12H3m15.364 6.364l-.707-.707M6.343 6.343l-.707-.707m12.728 0l-.707.707M6.343 17.657l-.707.707M16 12a4 4 0 11-8 0 4 4 0 018 0z"></path>
							</svg>
						{:else}
							<!-- Moon icon for dark mode -->
							<svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
								<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M20.354 15.354A9 9 0 018.646 3.646 9.003 9.003 0 0012 21a9.003 9.003 0 008.354-5.646z"></path>
							</svg>
						{/if}
						<span class="text-sm font-medium font-phillies">Switch Mode</span>
					</button>
				</div>
			</div>
			
		<!-- Search Bar - Always visible -->
        <div class="flex justify-center items-center gap-4">
            <input
              type="text"
              bind:value={searchQuery}
              onkeypress={handleKeyPress}
              placeholder="Search Google..."
              class="w-80 px-4 py-2 border border-slate-300 dark:border-slate-600 rounded-lg 
                     bg-white dark:bg-slate-800 text-slate-900 dark:text-slate-100 
                     focus:outline-none focus:ring-2 focus:ring-[var(--theme-primary)] focus:border-transparent"
            />
          
            <button
              onclick={handleSearch}
              class="px-6 py-2 rounded-lg transition-colors flex items-center space-x-2"
              style="background: var(--theme-primary); color: white; box-shadow: 0 4px 15px rgba(232, 24, 40, 0.3);"
            >
              <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  stroke-width="2"
                  d="M21 21l-6-6m2-5a7 7 0 11-14 0 7 7 0 0114 0z"
                />
              </svg>
              <span class="font-phillies">Search</span>
            </button>
          </div>
		</div>
	</div>
</header>
