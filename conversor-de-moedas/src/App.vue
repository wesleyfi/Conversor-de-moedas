<template>

        <div>
            <h1 >Conversor de Dogecoin</h1>
            <div id="main">
                  
                      <Conversor/>
                  
            </div>
        </div>
        
        
</template>

<script>
import "bootstrap/dist/css/bootstrap.css"
import "font-awesome/css/font-awesome.css"
import Conversor from "./components/Conversor.vue" 
export default {
 name: 'app',
 components: {
     Conversor
 }
}
</script>
<style>
    body{
        display: flex;
        justify-content: center;
        align-items: center;
        width: 100vw;
        height: 100vh;
        background-color: rgb(173, 238, 238);
    }
    
</style>
