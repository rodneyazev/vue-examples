<template>
    <div class="is-flex is-align-items-center is-justify-content-space-between">
        <Cronometro :tempoEmSegundos="tempoEmSegundos" />
        <button class="button" @click="iniciarContagem">
            <span class="icon">
                <i class="fas fa-play"></i>
            </span>
            <span>play</span>
        </button>
        <button class="button" @click="finalizarContagem">
            <span class="icon">
                <i class="fas fa-stop"></i>
            </span>
            <span>stop</span>
        </button>
    </div>
</template>

<script lang="ts">
    import { defineComponent } from 'vue';
    import Cronometro from './Cronometro.vue';

    export default defineComponent({
        name: 'Formulario',
        components: {
            Cronometro
        },
        data() {
            return {
                tempoEmSegundos: 0,
                cronometro: 0
            }
        },
        methods: {
            iniciarContagem() {
                // 1 seg = 1000 ms
                this.cronometro = setInterval(()=> {
                    this.tempoEmSegundos += 1;
                }, 1000)
            },
            finalizarContagem(){   
                clearInterval(this.cronometro);
            }
        }
    });
</script>