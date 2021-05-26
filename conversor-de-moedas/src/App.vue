<template>
        <div>
            <h1 class="text-center">Conversor de moedas</h1>
            <div id="main">
                  <div class="container">
                      <Conversor moeda-a="BRL" moeda-b="USD"/>
                      <Conversor moeda-a="USD" moeda-b="BRL"/>
                  </div>
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
      .container{
          display: flex;
          justify-content: center;
          align-items: center;
      }
</style>
