<script>
  import { onMount } from "svelte";
  
  let artista = [];
  onMount(async function() {
    await fetch(`http://localhost:8081/recomend`)
      .then(r => r.json())
      .then(data => {
        artista = data;
      });
  });
  let artistas = [];
  onMount(async function() {
	  const res = await fetch(`http://localhost:8888/Selena Gomez`);
		artistas = await res.json();
		console.log(artistas)
    
  });
</script>

<slot {artista}/>