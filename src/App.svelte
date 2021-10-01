<script>
    let buscarRecomendacoes = '';

	function handleSubmit() {
		alert(`"${buscarRecomendacoes}"`);
	}
	import { onMount } from 'svelte';

	let artistas = [];
	let textos = [];
  onMount(async function() {
	  const res = await fetch(`http://localhost:8888/recomend`);
		artistas = await res.json();
		textos =  JSON.stringify(artistas);
		console.log(artistas)
    
  });


	
</script>

<main>
   <form on:submit|preventDefault={handleSubmit}>
	<input type="search"  id="search" bind:value={buscarRecomendacoes} placeholder="Pesquisar">


	<button type=submit>
		Buscar
	</button>
    </form>
	<h1>Artistas recomendados</h1>
	
	{#each textos as texto}
		{texto}
	{/each}


 


	
	    
</main>

 <p> <textos></p>

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