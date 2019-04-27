<template>
  <div id="app">
      <h1>Tarefas</h1>
      <progresso-tarefas :progresso="progresso"/>
      <adicionar-tarefa @adicionar="adicionarTarefa"/>
      <lista-tarefas :tarefas="tarefas" @alterarStatus="alterarStatus" @removerTarefa="removerTarefa"/>
  </div>
</template>

<script>

import ListaTarefas from "./components/ListaTarefas";
import AdicionarTarefa from "./components/AdicionarTarefa";
import ProgressoTarefas from "./components/ProgressoTarefas";
export default {
    name: 'app',
    components: {
        ProgressoTarefas,
        AdicionarTarefa,
        ListaTarefas,
    },
    data() {
        //primeiro {conteudo:'teste', status:''}
        return{
            tarefas:[]
        }
    },
    created() {
      const jsonTarefas = localStorage.getItem('tarefas');
      const arrayTarefas = JSON.parse(jsonTarefas);
      this.tarefas = Array.isArray(arrayTarefas) ? arrayTarefas : [];
    },
    watch: {
      /*tarefas(){
          localStorage.setItem('tarefas', JSON.stringify(this.tarefas))
      }*/
      //tranforamar as arefas em um objeto
      tarefas: {
          deep: true,
          handler(){
              localStorage.setItem('tarefas', JSON.stringify(this.tarefas))
          }
      }
    },
    computed: {
      progresso() {
          let total = this.tarefas.length;
          let concluidas = this.tarefas.filter(t => !t.pendente).length;
          return Math.round(concluidas / total * 100) || 0;
      }
    },
    methods: {
        adicionarTarefa(tarefa) {
            const comparaConteudo = t => t.conteudo === tarefa.conteudo;
            const tarefaExiste = this.tarefas.filter(comparaConteudo).length == 0;
            if (tarefaExiste) {
                this.tarefas.push({
                    conteudo: tarefa.conteudo,
                    pendente: tarefa.pendente || true
                })
            }
        },
        removerTarefa(id) {
            //  quem eu quero excluir e quantos eu quero excluir
            //const i = this.tarefas.indexOf(tarefa)
            this.tarefas.splice(id, 1)
        },
        alterarStatus(id) {
            this.tarefas[id].pendente = !this.tarefas[id].pendente;
        }
    }
}
</script>

<style>
body {
  font-family: 'Lato', sans-serif;
  color: #4d4d4d;
}

#app {
  display: flex;
  flex: 1;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  /*height: 100vh;*/
}
.progresso {
  position: fixed;
  top: 0;
  bottom: 0;
}
#app h1 {
  display: flex;
  margin-bottom: 5px;
  font-weight: 300;
  font-size: 3rem;
}
</style>
