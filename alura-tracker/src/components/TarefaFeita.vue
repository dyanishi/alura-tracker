<template>
    <Box>
        <div class="div box has-text-weigth-bold">
            <div class="column is-7"> {{ tarefa.descricao || 'Tarefa sem descrição' }} </div>
            <div class="column">
                <CronometroTarefa :tempo-em-segundos="tarefa.duracaoEmSegundos" />
            </div>
        </div>
    </Box>
</template>

<script lang="ts">

import { defineComponent, PropType } from 'vue';
import CronometroTarefa from './CronometroTarefa.vue';
import ITarefa from '@/interfaces/ITarefa';

export default defineComponent({
    name: 'TarefaFeita',

    components: {
        CronometroTarefa
    },

    props: {
        tarefa: {
            type: Object as PropType<ITarefa>,
            required: true
        }
    }
})

</script>