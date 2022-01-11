<template>
   <div class="tarefas">
      <Progress :value="tarefasConcluidas" :max="tarefasTotal" />

      <div class="entrada">
         <input
            @keypress.enter="adicionarTarefa"
            ref="txt_tarefa"
            type="text"
            name=""
            id=""
            placeholder="Nova tarefa?"
         />
         <button @click="adicionarTarefa">+</button>
      </div>
      <br />
      <br />
      <div class="listaterefas">
         <Tarefa
            v-on:eventoExcluirTarefa="excluirTarefa"
            v-on:eventoMudouEstado="mudouEstado"
            v-for="(tarefa, index) in tarefas"
            :descricao="tarefa.descricao"
            :estado="tarefa.estado"
            :key="index"
            :id="index"
         />
      </div>
      <br />
      <br />
      <br />
   </div>
</template>

<script>
   import Tarefa from './Tarefa.vue'
   import Progress from './Progress.vue'
   export default {
      components: { Tarefa, Progress },
      data() {
         return {
            tarefas: [
               {
               }
            ]
         }
      },
      methods: {
         adicionarTarefa(e) {

            this.tarefas.push({
               descricao: this.$refs.txt_tarefa.value,
               estado: "ativa"
            })
            this.$refs.txt_tarefa.value = ""
         },
         excluirTarefa(ev) {
            this.tarefas = this.tarefas.filter((ob, index) => index != ev)
         },

         mudouEstado(ev) {
            console.log(ev);
            let elem = this.tarefas[ev]

            if (elem.estado == 'ativa')
               elem.estado = 'concluida';
            else
               elem.estado = 'ativa'

         }


      },
      computed: {
         tarefasConcluidas() {
            return 0 || this.tarefas.filter(tar => tar.estado == "concluida").length
         },
         tarefasTotal() {
            return 0 || this.tarefas.length
         }
      },
      watch: {
         tarefas: {
            deep: true,
            handler() {
               localStorage.setItem("tasks", JSON.stringify(this.tarefas))
            }
         }
      },
      created() {
         const json = localStorage.getItem("tasks");
         this.tarefas = JSON.parse(json) || [];
      }

   }
</script>

<style scoped>
   .tarefas {
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
   }
   .entrada input[type="text"] {
      font-size: 1.2rem;
      padding: 5px;
   }
   .entrada button {
      font-size: 1.2rem;
      border-radius: 0px 5px 5px 0px;
      background-color: dodgerblue;
      color: white;
      border: none;
      border-color: dodgerblue;
      padding: 7px 10px;
   }

   .listaterefas {
      display: flex;
      flex-direction: row;
      flex-wrap: wrap;
      justify-content: center;
      margin: 10px;
   }
</style>