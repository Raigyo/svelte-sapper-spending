<script>
	// import Nav from '../components/_Nav.svelte';

	// export let segment;
</script>

<style>
	main {
		position: relative;
		max-width: 56em;
		background-color: white;
		padding: 2em;
		margin: 0 auto;
		box-sizing: border-box;
	}
  ul a {
    margin: 15px;
  }
</style>

<nav>
	<ul>
    <a href="/">Accueil</a>
    <a href="/services">Services</a>
    <a href="/contact">Contact</a>
	</ul>
</nav>

<main>
	<slot></slot>
</main>