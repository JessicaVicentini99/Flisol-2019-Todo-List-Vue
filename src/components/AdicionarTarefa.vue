<template>
  <div class="row mb-3">
    <input  class="form-element" v-model="conteudo" @keydown.enter="adicionarTarefa" type="text">
    <button  class="form-element"  @click="adicionarTarefa">+</button>
  </div>
  
</template>

<script>
    export default {
        name: "AdicionarTarefa",
        data() {
            return {
                conteudo: ''
            }
        },
        methods: {
            adicionarTarefa() {
                this.$emit('adicionar', {conteudo: this.conteudo});
                this.conteudo = ''
            }
        }
    }
</script>

<style scoped>
  .nova-tarefa {
    margin: 35px;
  }
  
  .form-element {
    outline: none;
    border: 1px solid #4d4d4d;
    padding: 5px 10px 8px;
    color: #4d4d4d;
  }
  
  input.form-element {
    width: 500px;
    background: #FFF2;
    border-top-left-radius: 50px;
    border-bottom-left-radius: 50px;
  }
  
  button.form-element {
    border-left: none;
    color: #ffffff;
    background-color: #2196F3;
    border-top-right-radius: 50px;
    border-bottom-right-radius: 50px;
  }
</style>