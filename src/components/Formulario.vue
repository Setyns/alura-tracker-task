<template>
    <div class="box formulario">
        <div class="columns">
            <div class="column is-8" role="form" aria-label="Criar nova task">
                <input type="text" class="input" placeholder="Qual task voce deseja iniciar?" v-model="descricao">
            </div>
            <div class="column">
            </div>
           <Temporizador @aoTemporizadorFinalizado="finalizarTarefa"/>
            </div>
        </div>
</template>

<script lang="ts">

import { defineComponent } from 'vue'
import Temporizador from './Temporizador.vue';
export default defineComponent({
name: "TaskFormulario",
emits: ['aoSalvarTarefa'],
    components: {
        Temporizador
    },
    data () {
        return{
            descricao: ''
        }
    },
    methods: {
        finalizarTarefa (tempoDecorrido : number) : void  {
            this.$emit('aoSalvarTarefa',{
                duracaoEmSegundos: tempoDecorrido,
                descricao: this.descricao
            })
            this.descricao = ''

        }
    }
});
</script>

<style>
.formulario {
    color: var(--texto-primario);
    background-color: var(--bg-primario);
}
</style>
