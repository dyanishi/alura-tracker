<template>
    <div class="box-has-text-weigth-bold" :style="estilos"></div>
    <slot> </slot>
</template>

<script lang="ts" >
import { defineComponent } from 'vue';

export default defineComponent({
    name: 'BoxComponent',

    data() {
        return {
            estilos: {
                background: '#FAF0CA'
                //backgroundColor: '#FAF0CA'
                //background-color: '#FAF0CA'
            }
        }
    }
})

</script>
