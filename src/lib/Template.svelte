<script>
    import { createEventDispatcher } from "svelte";
    let p5="I certainly shall not. You know I detest it, unless I am particularly acquainted with me partner. At such an assembly as this it would be insupportable."
    let p4="In vain I have struggled. It will not do. My feelings will not be repressed. You must allow me to tell you how ardently I admire and love you.";
    let p3="Nothing is more deceitful…than the appearance of humility. It is often only carelessness of opinion, and sometimes an indirect boast.";
    let p1="For what do we live, but to make sport for our neighbors, and laugh at them in our turn?";
    let p2="Do not give way to useless alarm…though it is right to be prepared for the worst, there is no occasion to look on it as certain.";
    const dispatch=createEventDispatcher();
    
</script>
<div class="items-center hover:cursor-pointer ml-2 w-96">
    <div class="bg-emerald-200 p-2 rounded-lg">
        Click on anyone of following templates to try
    </div>
    <div contenteditable="false" bind:innerHTML={p1} on:keypress={()=>{dispatch('clicked',p1);}} on:click={()=>{dispatch('clicked',p1); console.log(1)}} class="hover:bg-emerald-100 mt-3"></div>
    <div contenteditable="false" bind:innerHTML={p2} on:keypress={()=>{dispatch('clicked',p2);}} on:click={()=>{dispatch('clicked',p2); console.log(2)}} class="hover:bg-emerald-100 mt-3"></div>
    <div contenteditable="false" bind:innerHTML={p3} on:keypress={()=>{dispatch('clicked',p3);}} on:click={()=>{dispatch('clicked',p3); console.log(3)}} class="hover:bg-emerald-100 mt-3"></div>
    <div contenteditable="false" bind:innerHTML={p4} on:keypress={()=>{dispatch('clicked',p4);}} on:click={()=>{dispatch('clicked',p4); console.log(4)}} class="hover:bg-emerald-100 mt-3"></div>
    <div contenteditable="false" bind:innerHTML={p5} on:keypress={()=>{dispatch('clicked',p5);}} on:click={()=>{dispatch('clicked',p5); console.log(5)}} class="hover:bg-emerald-100 mt-3"></div>


</div>
