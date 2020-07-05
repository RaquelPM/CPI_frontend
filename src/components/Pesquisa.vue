<template>
    <div>
        <Nav :pesquisa="pesquisa" />
        <div class="w-100 d-flex align-items-center justify-content-center flex-column">
            <div v-bind:class="{aparecer:pesquisa, sumir:!pesquisa}" class="d-flex flex-column w-50 align-items-center mt-4">
                <div id="lema" class="d-flex">
                    <p class="mr-2">Crie, Pesquise,</p>
                    <p class="font-weight-bold" >Inove</p>
                </div>
                <p id="description" class="text-center font-weight-light font-italic" > Desenvolva projetos de pesquisa de forma simples, rápida e organizada</p>
            </div>
            <div class="d-flex flex-column w-50 mt-3 align-items-center">
                <div class="w-100 d-flex justify-content-center">
                    <input v-on:click="pesq" placeholder="Eletrônica, Biologia.." class="bord_input ubuntu w-100 pl-2 py-3" id="input"  />
                    <button id="bt_pes" class="btn">a</button>
                </div>
                <v-combobox
                    v-if="!pesquisa"
                    class="w-100 mt-3"
                    :items="[{value: 0, text: 'Option 1'}, {value: 1, text: 'Option 2'}, {value: 2, text: 'Option 3'}]"
                    item-value="value"
                    label="Opções de filtro"
                ></v-combobox>
            </div>
            <img  width="200" height="150" class="mt-5" src="@/assets/Icon_PC.svg"/>
        </div>
    </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import Nav from './Nav.vue';


@Component({
    components:{
        Nav,
    }
})
export default class Pesquisa extends Vue {
    pesquisa=false;
    items: Array<string> = ['Foo', 'Bar', 'Fizz', 'Buzz'];

    pesq (): void {
        this.pesquisa=!this.pesquisa
      console.log(!this.pesquisa)    
    }
    
    created(){
        console.log(this.items)
        this.pesq();
    }
}
</script>

<style>

.sumir{
    transition: height 0.3s;
    overflow: hidden;
    height:0px;
}
.aparecer{
    transition: height 0.3s;
    overflow: hidden;
    height:200px;
}

#lema{
    font-size:45px;
    line-height:50px;
    font-family: Ubuntu;
}
#description{
    font-size:30px;
    font-family: 'Roboto', sans-serif;
}

#input{
    height:40px;
    border-top-left-radius: 7px;
    border-bottom-left-radius: 7px;
    font-size:20px;
}

#bt_pes{
    height:40px;
    background-color:#6CB2B2;
    border-top-right-radius: 7px;
    border-bottom-right-radius: 7px;
    border-top-left-radius: 0px;
    border-bottom-left-radius: 0px;
}

</style>
