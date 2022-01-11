<template>
   <div class="tarefa">
      <div>
         <span>{{ estado }}</span>
         <button v-on:click="excluirTarefas">X</button>
      </div>
      <div
         class="frame"
         :class="{ ativa: estado == 'ativa', concluida: estado == 'concluida' }"
         @click="mudaEstado"
      >
         <span class="">
            {{ descricao }}
         </span>
      </div>
   </div>
</template>

<script>
   export default {
      props: {
         descricao: {
            type: String,
            default: 'Vazio'
         },
         estado: {
            type: String,
            default: 'ativa'
         },
         id: {
            type: Number
         }
      },
      data() {
         return {

         }
      },
      methods: {
         excluirTarefas() {
            this.$emit("eventoExcluirTarefa", this.id)
         },
         mudaEstado() {
            this.$emit("eventoMudouEstado", this.id)
         }
      }
   }
</script>

<style scoped>
   .tarefa {
      width: 200px;
      /* height: 100px; */
      min-height: 100px;
      border-radius: 10px;
      color: white;
      font-weight: 800;
      display: flex;
      flex-direction: column;
      align-items: end;
      margin: 5px;
      background-color: #232729;
   }

   .frame.ativa {
      background-color: violet;
      border-color: blueviolet;
   }

   .frame.concluida {
      background-color: rgb(49, 207, 62);
      border-color: rgb(31, 153, 42);
      text-decoration: line-through;
   }

   .tarefa button {
      width: 22px;
      height: 22px;
      border: none;
      border-radius: 50%;
      margin: 8px;
      color: white;
      background-color: rgb(167, 93, 150);
      font-weight: bold;
   }

   .tarefa button:hover {
      background-color: rgb(136, 13, 33);
   }

   .frame {
      width: 100%;
      height: 100%;
      display: flex;
      flex-direction: row;
      justify-content: center;
      align-items: center;
      text-align: center;
      padding: 12px;
      margin-top: 0px;
      border-radius: 0px 0px 10px 10px;
      user-select: none;
      cursor: pointer;
   }
</style>