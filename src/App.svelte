<script>
	
	import Navbar from './components/Navbar.svelte';
	import Tarea from './components/Tarea.svelte';
</script>

<main class="fondo">
	<Navbar />
	<Tarea />
	
</main>

<style>
	.fondo {
		background-image: url(../assets/img/background.jpg);
		height: 100vh;
		background-size: cover;
		background-position: center;
	}
</style>