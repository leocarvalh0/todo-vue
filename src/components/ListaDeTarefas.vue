<script setup>
const props = defineProps(['tarefas', 'tarefasPendentes', 'filtro']);
</script>
<template>
    <p v-if="props.tarefasPendentes == 0 && props.filtro == 'pendentes'" class="mt-4 ms-2">Sem tarefas pendentes</p>
    <ul v-else class="list-group mt-4">
        <li class="list-group-item" v-for="tarefa in props.tarefas">
            <input @change="evento => tarefa.finalizada = evento.target.checked" :checked="tarefa.finalizada"
                :id="tarefa.titulo" type="checkbox">
            <label :class="{ done: tarefa.finalizada === true }" class="ms-3" :for="tarefa.titulo">
                {{ tarefa.titulo }}
            </label>
        </li>
    </ul>
</template>

<style scoped>
    .done {
        text-decoration: line-through;
    }
</style>