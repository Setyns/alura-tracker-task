<template>
<main class="columns is-gapless is-multiline" :class="{'modo-escuro': modoEscuroAtivo}">
    <div class= "column is-one-quarter">
      <BarraLateral @aoTemaAlterado="trocarTema"/>
    </div>
    <div class= "column is-three-quarter conteudo">
      <Formulario @aoSalvarTarefa="salvarTarefa"/>
      <div class="lista">
        <Tarefa  v-for="(tarefa, index) in tarefas" :key="index" :tarefa="tarefa"/>
      </div>
      <Box v-if="listaEstaVazia">
        Voce não esta muito produtivo hoje
      </Box>
  </div>
 </main>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import BarraLateral from './components/BarraLateral.vue'
import Formulario from './components/Formulario.vue'
import Tarefa from './components/Tarefa.vue'
import iTarefa from './interfaces/ITarefa';
import Box from './components/Box.vue';


export default defineComponent({
  name: 'App',
  components: {
    BarraLateral,
    Formulario,
    Tarefa,
    Box
  },
  data () {
    return{
      tarefas: [] as iTarefa[],
      modoEscuroAtivo: false
    }
  },
  computed: {
    listaEstaVazia () : boolean {
      return this.tarefas.length === 0 
    }
  },
  methods: {
    salvarTarefa (Tarefa: iTarefa) {
      this.tarefas.push(Tarefa)
    },
  trocarTema (modoEscuroAtivo: boolean) {
    this.modoEscuroAtivo = modoEscuroAtivo
  }
}
});
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.lista{
  padding: 1.25rem;
}

main {
  --bg-primario: #fff;
  --texto-primario: #000;
}

main.modo-escuro {
  --bg-primario: #2b2d42;
  --texto-primario: #ddd;

}

.conteudo {
  background-color: var(--bg-primario);
}
</style>
