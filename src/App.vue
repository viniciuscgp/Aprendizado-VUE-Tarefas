<template>
   <div class="" id="app">
      <div class="container">
         <h1>Tarefas</h1>
         <Tarefas />
      </div>
      <footer>
         <a href="https://twitter.com/viniciuscgp" target="_blank"
            >Me siga no twitter !</a
         >
      </footer>
   </div>
</template>

<script>
   import Tarefas from './components/Tarefas.vue'
   export default {
      components: { Tarefas },

   }
</script>

<style>
   body {
      font-family: "Lato", sans-serif;
      background: linear-gradient(to right, rgb(22, 34, 42), rgb(58, 96, 115));
      color: #fff;
   }

   .container {
      display: flex;
      flex: 1;
      flex-direction: column;
      justify-content: flex-start;
      align-items: center;
   }

   #app {
      height: 100vh;
   }

   #app h1 {
      margin-bottom: 5px;
      font-weight: 300;
      font-size: 3rem;
   }

   footer {
      display: flex;
      flex-direction: column;
      justify-content: center;
      background-color: rgb(43, 45, 49);
      height: 30px;
      text-align: center;
      font-size: small;
      position: fixed;
      width: 100vw;
      bottom: 0px;
   }
   footer > a {
      color: white;
      text-decoration: none;
   }
   footer > a:hover {
      color: yellow;
   }
</style>
