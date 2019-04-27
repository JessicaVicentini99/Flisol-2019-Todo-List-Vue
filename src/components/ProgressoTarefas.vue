<template>
  <div class="tarefa-progresso">
    <span class="valor-progresso">
      {{ progresso }}%
    </span>
    <div class="barra-progresso" :style="{width: progresso + '%'}"></div>
  </div>
</template>

<script>
    export default {
        name: "ProgressoTarefas",
        props: {
            progresso: {
                type: Number,
                default: 0
            }
        }
        
    }
</script>

<style scoped>
.tarefa-progresso {
  position: relative;
  width: 80%;
  color: #4d4d4d;
  height: 25px;
  background-color: rgba(0, 0, 0, 0.14);
  border-radius: 20px;
  margin-bottom: 15px;
  display: flex;
  flex-direction: column;
  align-items: center;
}
  
  .barra-progresso {
    position: absolute;
    border-radius: 25px;
    height: 25px;
    box-shadow: 0 5px 20px 0 rgba(0,0,0,.2), 0 13px 24px -11px rgba(3, 110, 217, 0.8);
    background:linear-gradient(135deg, #0FF0B3 0%,#036ED9 100%);
    align-self: flex-start;
  }

 .valor-progresso {
   z-index: 1;
 }
</style>