<template>
    <div class="lista-tarefa"><!--Primeira div-->
        <template v-if="tarefas.length">
            <tarefa v-for="(tarefa, id) in tarefas" :key="tarefa.conteudo" :tarefa="tarefa"
                    @removerTarefa="$emit('removerTarefa', id)"
                    @alterarStatus="$emit('alterarStatus', id)"/>
        </template>
        <p v-else class="titulo ">Sem tarefas</p>
    </div>
</template>

<script>
    import Tarefa from "./Tarefa";
    export default {
        name: "ListaTarefas",
        components: {Tarefa},
        props: { //primeiro o prop
            tarefas: {
                type: Array,
                required: true
            }
        }
    }
</script>

<style scoped>
    .lista-tarefa {
        display: flex;
        justify-content: center;
        flex-wrap: wrap;
    }

    .lista-tarefa .tarefa {
      margin: 10px;
    }
    
</style>