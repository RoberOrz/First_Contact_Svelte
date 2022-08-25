<script>
  export let character
</script>


<div
class="block w-full bg-white max-w-sm items-center justify-center text-center shadow-lg p-5 rounded-lg "
>
<img src={character.image} alt="" />

<h1
  class="items-center text-center mt-2 font-bold text-lg px-3 py-1 text-slate-600 bg-gray-200 rounded-md"
>
  {character.name}
</h1>
<div class="flex justify-center items-center py-3">
  {character.status}
  {#if character.status.length === 4}
    <div class="animate-pulse ml-1 rounded-full w-2 h-2 bg-red-500 " />
  {/if}
  {#if character.status.length === 5}
    <div
      class="animate-pulse ml-1 rounded-full w-2 h-2 bg-green-500 "
    />
  {/if}
  {#if character.status.length === 7}
    <div
      class="animate-pulse ml-1 rounded-full w-2 h-2 bg-yellow-500 "
    />
  {/if}
</div>

<div>
  <h6
    class="text-white bg-gradient-to-r from-sky-500 to-blue-600 p-2 rounded-md"
  >
    {character.species}
  </h6>
  <p class="p-2 border-[2px] rounded-md mt-4 text-gray-600">
    Origen: {character.origin.name}
  </p>
  <p class="p-2 border-[2px] rounded-md mt-4 text-gray-600">
    Ultima locación conocida: {character.location.name}
  </p>
</div>
</div>