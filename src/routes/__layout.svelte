<script>
	import Navbar from '$lib/components/Navbar.svelte';
	import '../app.css';
</script>

<Navbar />
<main class="container max-w-xl mx-auto px-4">
	<slot />
</main>
