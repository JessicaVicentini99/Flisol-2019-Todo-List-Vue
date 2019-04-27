<template>
  <div class="tarefa" @click="$emit('alterarStatus', tarefa)" :class="statusTarefa">
    <span @click.stop="$emit('removerTarefa', tarefa)" class="fechar">x</span>
    <p>{{ tarefa.conteudo }}</p><!--primeiro-->
  </div>
</template>

<script>
    export default {
        name: "Tarefa",
        props: {
            tarefa: {
                type: Object,
                required: true
            }
        },
        computed: { //segundo para trocar de classes
            statusTarefa() {
                return {
                    pendente: this.tarefa.pendente,
                    concluido: !this.tarefa.pendente
                }
            }
        }
    }
</script>

<style scoped>
  .tarefa {
    color: #ffffff;
    position: relative;
    box-sizing: border-box;
    width: 300px;
    height: 125px;
    padding: 10px;
    border-radius: 20px;
    font-size: 25px;
    font-weight: 300;
    cursor: pointer;
    user-select: none;
    display: flex;
    justify-content: center;
    align-items: center;
    word-wrap: break-word;
  }
  
  .pendente {
    box-shadow: 0 5px 20px 0 rgba(0,0,0,.2), 0 13px 24px -11px rgba(161, 5, 29, 0.8);
    background:linear-gradient(135deg, #F5515F 0%,#A1051D 100%);
   }

  .concluido {
    box-shadow: 0 5px 20px 0 rgba(0,0,0,.2), 0 13px 24px -11px rgba(69, 149, 34, 0.8);
    background:linear-gradient(135deg, #b1ea4d 0%,#459522 100%);
    text-decoration: line-through;
  }
  
  .pendente .fechar{
    background-color: #a1143a;
  }

  .concluido .fechar{
    background-color: #298629;
  }
  
  .fechar {
    position: absolute;
    right: 10px;
    top: 10px;
    font-size: 20px;
    font-weight: 600;
    height: 25px;
    width: 25px;
    border-radius: 25px;
    display: flex;
    justify-content: center;
  }
</style>