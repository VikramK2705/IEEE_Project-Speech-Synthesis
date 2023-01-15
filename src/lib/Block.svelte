<div class="shadow-md border mx-14 items-center relative" >
   
<div class="flex bg-zinc-300">
    <button on:click={remove} class="absolute right-0 top-0 -mt-7 rounded-full text-center bg-red-500 text-small text-white hover:bg-red-700" >x</button>

    <!-- rate button -->
    <div class="form-group"> 
        <label for="rate">Rate</label>
        <!-- <div id="rate-value" class="badge badge-primary bg-yellow-400 mx-5 justify-between" style="float: right;">1</div> -->
        <input type=number id="rate-value" bind:value={r_range} step="0.1" min=0 max=2 class=" bg-slate-400" style="float: right;">
        <input type="range" id="rate" bind:value={r_range} class="form-range" min="0.5" max="2" step="0.1">
    </div>
    <!-- pitch button -->
    <div class="form-group">
        <label for="pitch">Pitch</label>
        <input type=number id="pitch-value" bind:value={p_range} step="0.1" min=0 max=2 class=" bg-slate-400" style="float: right;">
        <input type="range" id="pitch" bind:value={p_range} class="form-range" min="0" max="2" step="0.1">
    </div>

</div>
<form>
<div class="form-group">
    <textarea name="" id="text-input" style="margin:20px" class="form-control form-control-lg" placeholder="Type Anything Here..."></textarea>
   </div>
    
    <button type="submit" class="inline-flex items-center px-5 py-2.5 text-sm font-medium text-center text-white bg-blue-700 rounded-lg focus:ring-4 focus:ring-blue-200 dark:focus:ring-blue-900 hover:bg-blue-800">
        Play
    </button>
 </form>
</div>
<script>
    let p_range=1,r_range=1;
    import { createEventDispatcher } from "svelte";
const dispatch=createEventDispatcher();
   const remove=()=>{
    dispatch('remove',block.id);
   };
   export let block,i;
</script>