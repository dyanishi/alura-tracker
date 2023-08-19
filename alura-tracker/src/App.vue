<template>
  <main class="columns is-gapless is-multiline" :class="{ 'modo-escuro': modoEscuroAtivo }">
    <div class="column is-one-quarter">
      <BarraLateral @aoTemaAlterado="trocarTema" />
    </div>
    <div class="column is-theree-quarter conteudo">
      <FormularioTarefa @aoSalvarTarefa="salvarTarefa" />
      <div class="lista">
        <div class="box has-text-weight-bold">
          <TarefaFeita v-for="(tarefa, index) in tarefas" :key="index" :tarefa="tarefa" />
          <BoxComponent v-if="listaEstaVazia">
            Você não está muito produtivo hoje
          </BoxComponent>
        </div>
      </div>
    </div>

  </main>
</template>

<script lang="ts">
import { computed, defineComponent } from 'vue'
import BarraLateral from './components/BarraLateral.vue'
import FormularioTarefa from './components/FormularioTarefa.vue'
import TarefaFeita from './components/TarefaFeita.vue'
import ITarefa from './interfaces/ITarefa'
import BoxComponent from './components/BoxComponent.vue'

export default defineComponent({
  name: 'App',

  components: {
    BarraLateral,
    FormularioTarefa,
    TarefaFeita,
    BoxComponent
  },

  data() {
    return {
      tarefas: [] as ITarefa[],
      modoEscuroAtivo: false
    }
  },

  methods: {
    salvarTarefa(tarefa: ITarefa) {
      this.tarefas.push(tarefa)
    },

    trocarTema(modoEscuroAtivo: boolean) {
      this.modoEscuroAtivo = modoEscuroAtivo;
    }
  },

  computed: {
    listaEstaVazia(): boolean {
      return this.tarefas.length == 0
    }
  },

});
</script>

<style>
.lista {
  padding: 1.25rem;
}

main {
  --bg-primario: #fff;
  --text-primario: #000;
}

main.modo-escuro {
  --bg-primario: #2b2d42;
  --text-primario: #ddd;
}

.conteudo {
  background-color: var(--bg-primario);
}
</style>
