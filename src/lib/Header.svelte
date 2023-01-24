<script>
  import logo from '../assets/logo.jpg';
  import { writable } from 'svelte/store';
  import Modal, { bind } from 'svelte-simple-modal';
  import Popup from './Popup.svelte';
  import { onMount } from 'svelte';
  const modal = writable(null);
  const showModal = () => modal.set(Popup);
  onMount(()=>{
      showModal
  });
</script>
<div class="header float-left flex">
    
      
    <div class="logo" style="">
    <img class="image" src={logo} width="60" height="60" alt="logo" style="border-radius:100"></div>
    <div class="speech">
    <center><h1 class="-mt-4 ml-96" style="font-size:3em" data-text="Speech Synthesizer.......">&nbsp;Speech Synthesiser</h1></center></div>  
  </div>
  <Modal show={$modal}>
    <button class=" mt-12 " style="background-color:floralwhite; padding:0.5em" on:click={showModal}>Know More</button>
  </Modal>
  
<style>
    .header {  
    width: 100%;
    background: bg-blue-300(220, 245, 242);
    color: aliceblue;
    font-size: 20px;
    height: 80px;
    float: none;  
    top: 0em;
    position: absolute;
    left:0em
}
.speech{
    float: inline-end;
}
.image{
    float: left;
    margin-top: 0;border-radius: 10px;
}

h1 {
    color: rgb(255, 255, 255);
    -webkit-text-stroke: 2px black;
    text-transform: uppercase;
    text-shadow: 8px 8px 10px black;
    padding-top: 10px;
    
}

</style>