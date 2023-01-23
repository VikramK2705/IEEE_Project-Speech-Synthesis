<script>
    import { createEventDispatcher } from "svelte";


    let p="Hello There";
    let p1="Heaven";
    let p2="Heathen";
    export {p};
    const dispatch=createEventDispatcher();
    
</script>
<div class="items-center hover:cursor-pointer ml-2 w-full">
    <div class="bg-red-400 p-2 rounded-lg">
        Click on anyone of following templates to try
    </div>
    <div contenteditable="false" bind:innerHTML={p1} on:keypress={()=>{dispatch('clicked',p1);}} on:click={()=>{dispatch('clicked',p1); console.log(1)}} class="hover:bg-lime-400"></div>
    <div contenteditable="false" bind:innerHTML={p2} on:keypress={()=>{dispatch('clicked',p2);}} on:click={()=>{dispatch('clicked',p2); console.log(2)}} class="hover:bg-lime-400"></div>

</div>
