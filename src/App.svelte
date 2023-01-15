<script>
  import Block from './lib/Block.svelte';
    import Header from './lib/Header.svelte';
  let blocks=[{id:1},{id:2},{id:3},{id:4},];
  let i=0;

  $: filteredBlocks=blocks;
    const getUsers=()=>{
      return filteredBlocks;
    };
    
    const remove=({detail})=>{
      blocks=blocks.filter((block)=>block.id !==detail)
    
    }
</script>

<main>
  <Header/>
  <div>
{#each filteredBlocks as block,i(block.id)}
{i+1}
<Block on:remove={remove} {block} {i}/>
{:else}
<p>No blocks available</p>
{/each}
</div>

</main>


