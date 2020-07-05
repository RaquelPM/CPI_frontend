<template>
<div class="position-relative d-flex">
    <!-- Input propriamente dito -->
    <input
        v-bind:class="{leftInput: isIconLeft, rightInput: isIconRight}"
        v-model="input_data"
        :placeholder="placeholder"
        class="w-100 py-1 px-3"
    >

    <!-- Container no ícone -->
    <div
        v-bind:class="{leftIcon: isIconLeft, rightIcon: isIconRight}"
        class="icon-container d-flex align-items-center justify-content-center"
    >
        <!-- Ícone passado como input -->
        <slot />
    </div>    
</div>
</template>

<script lang="ts">
import Vue from 'vue'
import { Component, Prop, Watch } from 'vue-property-decorator';

@Component
export default class Input extends Vue {
    // Propriedades de entrada
    @Prop({default: 'left'}) side?: 'right'|'left';
    @Prop() placeholder?: string;

    //Armazena os dados digitados
    input_data?: string = '';

    // Métodos computados para estilização
    get isIconLeft() {
        return this.side == 'left';
    }
    get isIconRight() {
        return this.side == 'right';
    }

    //Observa a mudança de dados
    @Watch('input_data')
    dataChanged(value: string) {
        this.$emit('change', value);
    }
}


</script>

<style scoped>
/* Estilo padrão de input */
input {
    top: 0;
    border-radius: 5px;
    background-color:#E1E1E1;
    border: 3px solid transparent;
    transition: all .1s;
}
/* Estilo padrão do container de ícon */
.icon-container {
    border-radius: 5px 0px 0px 5px;
    width: 50px;
    background-color: var(--primary);
    height: 100%;
    position: absolute;
    z-index: -1;
}
/* Estilo padrão do input ao ser focado */
input:focus {
    background-color: white;
    border-color: var(--primary);
}

.leftIcon {
    left: 0;
    border-radius: 5px 0px 0px 5px;
}
.rightIcon {
    right: 0;
    border-radius: 0px 5px 5px 0px;
}

.leftInput:focus {
    border-radius: 0px 5px 5px 0px;
    margin-left: 50px;
}
.rightInput:focus {
    border-radius: 5px 0px 0px 5px;
    margin-right: 50px;
}
</style>