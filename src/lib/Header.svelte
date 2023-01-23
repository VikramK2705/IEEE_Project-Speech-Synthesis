<script>
    import logo from '../assets/logo.jpg';
</script>
<div class="header float-left">
    <div class="logo">
    <img class="image" src={logo} width="80" height="80" alt="logo" style="border-radius:0"></div>
    <div class="speech">
    <h1 class="-mt-4" data-text="Speech Synthesizer.......">&nbsp;Speech Synthesiser</h1></div>   
  </div>

<style>
    .header {  
    width: 100%;
    background: beige;
    color: aliceblue;
    font-size: 20px;
    height: 80px;
    float: right;  
    top: 0em;
    position: absolute;
    left:0em
}
.speech{
    float: left;
}
.image{
    float: left;
    margin-top: 0;border-radius: 10px;
}

h1 {
    color: red;
    -webkit-text-stroke: 2px black;
    text-transform: uppercase;
    text-shadow: 8px 8px 10px black;
    padding-top: 10px;
    
}
h1 ::before {
    content: attr(data-text);
    position: relative;
    top: 0;
    left: 0;
    width: 0;
    height: 100%;
    color: red;
    -webkit-text-stroke: 2px black;
    border-right: 1px solid red;
    overflow: hidden;
    
}
</style>