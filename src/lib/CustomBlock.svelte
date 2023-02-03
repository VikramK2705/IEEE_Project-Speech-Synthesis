<body style="" class=""><div class="shadow-md border relative h-96 mx-14 " >
    
    <div class="flex bg-zinc-300">
       
        <button on:click={remove} class="absolute right-0 top-0 -mt-0 -mr-6 text-center btn btn-outline-danger btn-sm" >x</button>
        <!-- rate button -->
        <div class="form-group rounded-3xl"> 
            <label for="rate">Rate</label>
            <input type=number id="rate-value" bind:value={r_range} step="0.1" min=0.1 max=2 class=" text-center bg-slate-400" style="float: right;">
            <input type="range" id="rate" bind:value={r_range} class="form-range " min="0.5" max="3" step="0.5">
        </div>
        <!-- pitch button -->
        <div class="form-group">
            <label for="pitch">Pitch</label>
            <input type=number id="pitch-value" bind:value={p_range} step="0.1" min=0 max=2 class=" bg-slate-400 text-center" style="float: right;">
            <input type="range" id="pitch" bind:value={p_range} class="form-range" min="0" max="2" step="0.1">
        </div>
        <!-- volume button -->
        <div class="form-group">
            <label for="pitch">Volume</label>
            <input type=number id="volume-value" bind:value={v_range} step="0.1" min=0 max=1 class=" bg-slate-400 text-center" style="float: right;">
            <input type="range" id="volume" bind:value={v_range} class="form-range" min="0" max="1" step="0.1">
           </div>
    
    </div>
    <form id="text-box" on:submit|preventDefault={speak}>
    <div class="form-group h-52">
        <textarea name="" id="text-input" style="" bind:value={speakText} class="form-control form-control-lg px-2 m-0 mt-1 h-52" placeholder="Type Anything Here..."></textarea>
       </div>
        <div class="m-1 mt-3">
        <button type="submit"  class="inline-flex mx-2 items-center px-5 py-2.5 text-sm  font-medium text-center text-white bg-blue-700 rounded-lg focus:ring-4 focus:ring-blue-200 dark:focus:ring-blue-900 hover:bg-blue-800">
            Play
        </button>
        <button type="button" on:click={pause} class="inline-flex mx-2 items-center px-5 py-2.5 text-sm font-medium text-center text-white bg-blue-700 rounded-lg focus:ring-4 focus:ring-blue-200 dark:focus:ring-blue-900 hover:bg-blue-800">
            {state?'Pause':'Resume'}
        </button>
        <button type="button" on:click={stop} class="inline-flex mx-2 items-center px-5 py-2.5 text-sm font-medium text-center text-white bg-blue-700 rounded-lg focus:ring-4 focus:ring-blue-200 dark:focus:ring-blue-900 hover:bg-blue-800">
            Stop
        </button>
       </div>
        
      </form>
      <button type="submit" on:click={()=>{speakText=""}} class="inline-flex m-0 items-center px-3 py-1 text-sm font-medium text-center text-zinc-900 bg-slate-300 rounded-lg focus:ring-4 focus:ring-blue-200 hover:bg-slate-500">
        Clear All
    </button>
     </div>  
    
    </body>
    <script >
     //For deleting blocks
      import { createEventDispatcher} from "svelte";
    
      const dispatch=createEventDispatcher();
      const remove=()=>{
        dispatch('remove',custblock.iden);
       };
       let p_range=1,r_range=1,v_range=0.5;
       export let custblock,playVoice;
       export let j;
       let speakText;
       if(custblock.statement===null){
          speakText="";
          console.log(speakText);
       }
       else{
         speakText=custblock.statement;
         console.log(speakText);
       }
       

       
    //Initialize WebSpeech API
    const synth=window.speechSynthesis;
     $:state=true;
     var i=0;
     const utterThis=new SpeechSynthesisUtterance(speakText);
    
    const pause=()=>{
        if(synth.paused){
            state=true;
            utterThis.voice=playVoice;
            utterThis.rate=r_range;
            utterThis.pitch=p_range;
            utterThis.volume=v_range;
            console.log("resumed");
            synth.resume();
        }
        else{
            state=false;
            console.log(i);
            i=i+1;
            console.log("paused");
            if(i>=2){
                i=0;
                state=true;
                utterThis.voice=playVoice;
            utterThis.rate=r_range;
            utterThis.pitch=p_range;
            utterThis.volume=v_range;
                synth.resume();

            }
            else{
            synth.pause();
            }

        }
    }
    const stop=()=>{
        synth.cancel();
        state=true;
    }
    
    //Speak
    const speak=()=>{
        const utterThis=new SpeechSynthesisUtterance(speakText);
        state=true;
        //Initialising Voice
        utterThis.voice=playVoice;
        //Check if speaking
        if(synth.speaking){
            console.error('Already speaking...');
            synth.cancel();
            synth.speak(utterThis);
            return;
        }
        
         
        if(speakText !==''){
                
            //Speak end
            utterThis.onend=e=>{
                console.log('Done speaking...');
                state=true;
                synth.cancel();
                // body.style.background='#141414 ';
            }
            
            //Speak Error
            utterThis.onerror =e=>{
                console.error('Something went wrong');
                synth.cancel();
            }
            speakText.onend = function(event) {
                console.log(event.name + ' boundary reached after ' + event.elapsedTime + ' seconds.');
              }
          
          
            //Set pitch and rate
            utterThis.rate=r_range;
            utterThis.pitch=p_range;
            utterThis.volume=v_range;
    
            //Speak
            synth.speak(utterThis);
            console.log("Speaking");
        }
        else{
            alert("Type something to say....");
        }
       
    };
    
    
    </script>
    
    <style>
        body {
        margin: 0;
        display: flex;
        place-items: center;
        min-width: 350px;
        min-height: fit-content;
    }
    #text-input{
        
        border-radius: 5px;
        background: beige;
        color: black;
        overflow: scroll;
        font-size: 20px;
        resize: none;
        box-shadow: 12px 12px 5px rgb(148, 111, 111);
    }
    </style>