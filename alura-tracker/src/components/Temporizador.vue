<template>
    <div class="is-flex is-align-items-center is-justify-content-space-between">
        <CronometroTarefa :tempo-em-segundos="tempoEmSegundos" />
        <button class="button" @click="iniciar" :disabled="cronometroRodando">
            <span class="icon">
                <i class="fas fa-play"></i>
            </span>
            <span>play</span>
        </button>
        <button class="button" @click="finalizar" :disabled="!cronometroRodando">
            <span class="icon">
                <i class="fas fa-stop"></i>
            </span>
            <span>stop</span>
        </button>
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import CronometroTarefa from './CronometroTarefa.vue';

export default defineComponent({
    name: 'TemporizadorFormulario',

    emits: ['aoTemporizadorFinalizado'],

    components: {
        CronometroTarefa
    },

    data() {
        return {
            tempoEmSegundos: 0,
            cronometro: 0,
            cronometroRodando: false
        }

    },

    methods: {
        iniciar() {
            //começar contagem
            //1s = 1000ms
            this.cronometro = setInterval(() => {
                this.tempoEmSegundos += 1
            }, 1000);
            this.cronometroRodando = true;

        },

        finalizar() {
            clearInterval(this.cronometro);
            this.cronometroRodando = false;

            this.$emit("aoTemporizadorFinalizado", this.tempoEmSegundos);
            this.tempoEmSegundos = 0;

        }
    }
});
</script>