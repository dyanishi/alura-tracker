<template>
    <FormularioTarefa @aoSalvarTarefa="salvarTarefa" />
    <div class="lista">
        <BoxComponent v-if="listaEstaVazia">
            Você não está muito produtivo hoje
        </BoxComponent>
        <TarefaFeita v-for="(tarefa, index) in tarefas" :tarefa="tarefa" :key="index" />
    </div>
</template>
  
<script lang="ts">
import { defineComponent } from 'vue'
import FormularioTarefa from '../components/FormularioTarefa.vue'
import TarefaFeita from '../components/TarefaFeita.vue'
import ITarefa from '../interfaces/ITarefa'
import BoxComponent from '../components/BoxComponent.vue'

export default defineComponent({
    name: 'App',

    components: {
        FormularioTarefa,
        TarefaFeita,
        BoxComponent
    },

    data() {
        return {
            tarefas: [] as ITarefa[]
        }
    },

    methods: {
        salvarTarefa(tarefa: ITarefa): void {
            this.tarefas.push(tarefa)
        }
    },

    computed: {
        listaEstaVazia(): boolean {
            return this.tarefas.length == 0
        }
    }
});
</script>