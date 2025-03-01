<template>
    <Box>
        <div class="columns">
            <div class="column is-7"> {{ tarefa.descricao || 'Tarefa sem descrição' }} </div>
            <div class="column">
                <Cronometro :tempoEmSegundos="tarefa.duracaoEmSegundos" />


            </div>
        </div>
    </Box>
</template>

<script lang="ts">
import { defineComponent, PropType } from 'vue';
import Cronometro from './Cronometro.vue';
import iTarefa from '@/interfaces/ITarefa';
import Box from './Box.vue';

export default defineComponent({
    name: "TarefaTask",
    components: {
        Cronometro,
    },
    props: {
        tarefa: {
            type: Object as PropType<iTarefa>,
            required: true
        }
    }
})

</script>
