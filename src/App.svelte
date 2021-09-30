<script>
    let busca = '';

	function handleSubmit() {
		alert(`"${busca}"`);
	}
	import { onMount } from 'svelte';

	let artistas = [];
	let texto = [];
  onMount(async function() {
	  const res = await fetch(`http://localhost:8888/recomend`);
		artistas = await res.json();
		texto =  JSON.stringify(artistas);
		console.log(artistas)
    
  });


	
</script>

<main>
   <form on:submit|preventDefault={handleSubmit}>
	<input type="search"  id="search" bind:value={busca} placeholder="Pesquisar">


	<button type=submit>
		Buscar
	</button>
    </form>
	<h1>Artistas recomendados</h1>


<ul>
	{artistas}
</ul>
	
	    
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}
	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
      li{
        list-style: none;
      }
	input{
		
		 width: 400px;
	}
	
</style>