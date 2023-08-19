<template>
    <BoxComponent>
        <div class="columns">
            <div class="column is-7"> {{ tarefa.descricao || 'Tarefa sem descrição' }} </div>
            <div class="column">
                <CronometroTarefa :tempo-em-segundos="tarefa.duracaoEmSegundos" />
            </div>
        </div>
    </BoxComponent>
</template>

<script lang="ts">

import { defineComponent, PropType } from 'vue';
import CronometroTarefa from './CronometroTarefa.vue';
import ITarefa from '@/interfaces/ITarefa';
import BoxComponent from './BoxComponent.vue';

export default defineComponent({
    name: 'TarefaFeita',

    components: {
        CronometroTarefa,
        BoxComponent
    },

    props: {
        tarefa: {
            type: Object as PropType<ITarefa>,
            required: true
        }
    }
});

</script>