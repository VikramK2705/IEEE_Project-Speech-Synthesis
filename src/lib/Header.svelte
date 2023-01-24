<script>
    import logo from '../assets/logo.jpg';
</script>
<div class="header float-left">
    <div class="logo">
    <img class="image" src={logo} width="60" height="60" alt="logo" style="border-radius:100"></div>
    <div class="speech">
    <h1 class="-mt-4" data-text="Speech Synthesizer.......">&nbsp;Speech Synthesiser</h1></div>   
  </div>

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
h1 ::before {
    content: attr(data-text);
    position: absolute;
    top: 0;
    left: 0;
    width: 0;
    height: 100%;
    color: rgb(255, 255, 255);
    -webkit-text-stroke: 2px black;
    border-right: 1px solid rgb(0, 0, 0);
    overflow: hidden;
    
}
</style>