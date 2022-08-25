<script>
  import Card from './lib/Card.svelte'
  let characters = [];
  let counter = 1
  const handleClickMore = () => {
    counter++
    restApiRickandMorty()
  }
  const handleClickless = () => {
      counter--
      restApiRickandMorty()
  }


  async function restApiRickandMorty() {
    const res = await fetch(
      "https://rickandmortyapi.com/api/character?page=" + counter
    );
    const data = await res.json();
    characters = data.results;
  }
  restApiRickandMorty();
</script>

<main class="items-center justify-center">
  <div
    class="z-20 fixed top-0 left-0 right-0 text-center text-3xl font-bold bg-white/90 backdrop-blur-md p-4 rounded-md drop-shadow-md mx-auto max-w-sm"
  >
    <h1 class="text-slate-700">Rick & Morty API</h1>
  </div>
  <div class="flex items-center justify-center mt-[120px] mb-[10px]">
    <h1>Página {counter}</h1>    
  </div>
  <div class="items-center gap-10 justify-center flex ">
    
    <button
    on:click={handleClickless} 
    class="px-5 py-1 border rounded-md hover:bg-gray-100 disabled:text-gray-300 disabled:hover:bg-white" disabled={counter ===1}>Anterior</button>
    <button
    on:click={handleClickMore} 
    class="px-5 py-1 border rounded-md hover:bg-gray-100 disabled:text-gray-300 disabled:hover:bg-white" disabled={counter>=19}>Siguiente</button>
  </div>
  <div
    class="grid grid-cols-2 md:grid-cols-4 gap-6 md:gap-10 mt-[60px] max-w-screen-xl mx-auto"
  >
    {#each characters as character}
      <Card character={character}/>      
    {/each}
  </div>
</main>
