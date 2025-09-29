<script>
	let { title } = $props();
</script>

<header class="bg-white shadow-sm border-b">
	<div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
		<div class="flex justify-between items-center py-6">
			<div class="flex items-center">
				<h1 class="text-2xl font-bold text-gray-900">{title}</h1>
			</div>
			<nav class="hidden md:flex space-x-8">
				<a href="/" class="text-gray-500 hover:text-gray-900 transition-colors">Home</a>
				<a href="/about" class="text-gray-500 hover:text-gray-900 transition-colors">About</a>
				<a href="/contact" class="text-gray-500 hover:text-gray-900 transition-colors">Contact</a>
			</nav>
		</div>
	</div>
</header>
