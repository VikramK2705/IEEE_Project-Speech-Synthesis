<script>
    import { createEventDispatcher } from "svelte";
    const dispatch=createEventDispatcher();
    //  export let block,i;
    const synth=window.speechSynthesis;
    let voices=[];
    let initial=true;
    let selected;
    export {selected};
    voices=synth.getVoices();
    
    synth.onvoiceschanged=()=>{
         voices=synth.getVoices();
         if(initial){
         selected=voices[0];
         initial=false;
         }
         dispatch('selectedVoice',selected);
         
    }
     
  const selectedVoice=()=>{
    dispatch('selectedVoice',selected);
   };
   if(selected!=undefined){
    selectedVoice();
  }
  
  </script>
  

    <select bind:value={selected} on:change={selectedVoice} on:load={selectedVoice}  style="left:0em; background:white">
        {#each voices as voice}
            <option value={voice}>
                {voice.name}
            </option>
        {/each}
    </select>
  

