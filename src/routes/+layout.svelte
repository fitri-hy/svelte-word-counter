<script>
	import Header from './Header.svelte';
	import './styles.css';
</script>

<div class="w-full">
	<Header />

	<main class="w-full">
		<slot />
	</main>
</div>