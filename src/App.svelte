<script>
  import Block from './lib/Block.svelte';
  import Voices from './lib/Voices.svelte';
  import Header from './lib/Header.svelte';
    import Template from './lib/Template.svelte';
    import { slide,fly } from 'svelte/transition';
    import CustomBlock from './lib/CustomBlock.svelte';
    import { onMount } from 'svelte';
    import Footer from './lib/Footer.svelte';

  let selected;
  let p;
  $:stat1="";
  $: playVoice=""; 
  $: blockAvail=true;
 
  const handleVoice=(e)=>{
       console.log(e.detail);
       playVoice=e.detail;
  }

  let customblocks=[{iden:1,statement:null}];
  const clickHandle=(f)=>{
      stat1=f.detail;
      customblocks=[{iden:customblocks.length+1,statement:f.detail},...customblocks,];
    }
  
  
  let j;

  $: filteredBlocks=customblocks;
    
    const remove=({detail})=>{
      customblocks=customblocks.filter((customblock)=>customblock.iden !==detail)
      console.log(detail);
      if(customblocks.length==0){
        blockAvail=false;
      }
    }
    const add=()=>{
      customblocks=[{iden:customblocks.length+1,statement:null},...customblocks,];
    }
    onMount(()=>{
      
    });
</script>
<main class="content">
  
  <Header />

  <button class=" border-amber-600 my-1 bg-orange-300 hover:bg-orange-600 font-bold " id={blockAvail?'divfix':''} type='button' on:click={add}>Add a Block</button>
  <div class=" relative m-5 " style="left:0em">
    <Voices on:selectedVoice={handleVoice} {selected}/>
  <p class="bg-yellow-300 w-96 ml-96 rounded-2xl mt-1 ">Select the voices from above Drop Down List</p>
  </div>
  <div class="flex">
  
    <div class="">
     
     {#each filteredBlocks as custblock,j(custblock.iden)}

   <div transition:slide={{duration:800}} class="mx-6">
  <div class="bg-white w-full mt-4">
    {j+1}
            </div>
            <CustomBlock on:remove={remove} {custblock} {j}  {playVoice} />
            </div>

      {:else}
          
          <div class="ml-2 text-center">
          <h3 >No blocks available. Click the button above to add them.</h3>
          </div>
      {/each}
            
    </div>
    <div class="mx-6 border border-solid border-lime-600 px-6 py-3 relative m-2 right-0" >
      <Template on:clicked={clickHandle} {p}/>
      <p>{stat1}</p>
    </div>
</div>



<Footer />
</main>

<style>
  
  #divfix {
       bottom: 3rem;
       right: 3rem;
       position: fixed;
       z-index: 3000;
}
.content {
    width: 100%;
    
    background-image: linear-gradient(to bottom right,rgb(148, 111, 111),beige);
  
   
}

</style>