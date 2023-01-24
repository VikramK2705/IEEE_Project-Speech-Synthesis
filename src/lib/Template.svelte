<script>
    import { createEventDispatcher } from "svelte";


    let p="Hello There";
    let p1="For what do we live, but to make sport for our neighbors, and laugh at them in our turn?";
    let p2="Do not give way to useless alarm…though it is right to be prepared for the worst, there is no occasion to look on it as certain.";
    export {p};
    const dispatch=createEventDispatcher();
    
</script>
<div class="items-center hover:cursor-pointer ml-2 w-96">
    <div class="bg-emerald-200 p-2 rounded-lg">
        Click on anyone of following templates to try
    </div>
    <div contenteditable="false" bind:innerHTML={p1} on:keypress={()=>{dispatch('clicked',p1);}} on:click={()=>{dispatch('clicked',p1); console.log(1)}} class="hover:bg-emerald-100 mt-3"></div>
    <div contenteditable="false" bind:innerHTML={p2} on:keypress={()=>{dispatch('clicked',p2);}} on:click={()=>{dispatch('clicked',p2); console.log(2)}} class="hover:bg-emerald-100 mt-3"></div>

</div>
