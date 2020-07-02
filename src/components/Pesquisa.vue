<template>
    <div>
        <Nav :pesquisa="pesquisa" />
        <div class="w-100 d-flex align-items-center justify-content-center flex-column">
            <div v-bind:class="{aparecer:pesquisa, sumir:!pesquisa}" class="d-flex flex-column w-50 align-items-center mt-4">
                <div id="lema" class="d-flex">
                    <p class="mr-2">Crie, Pesquise,</p>
                    <p class="font-weight-bold" >Inove</p>
                </div>
                <p id="description" class="text-italic" > Desenvolva projetos de pesquisa de forma simples, rápida e organizada</p>
            </div>
            <div class="d-flex w-50 mt-3 justify-content-center" >
                <input v-on:click="pesq" placeholder="Eletrônica, Biologia.." class="input w-75 pl-2" id="input"  />
                <button id="bt_pes" class="btn">a</button>
            </div>
            <img  width="230" height="170" class="mt-3" src="@/assets/Icon_PC.svg"/>
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
    pesquisa=true;

    pesq (): void {
        this.pesquisa=!this.pesquisa
      console.log(!this.pesquisa)    
    }
    
    created(){
        this.pesq();
    }
}
</script>

<style>
.sumir{
    transition: height 0.5s;
    overflow: hidden;
    height:0px;
}
.aparecer{
    transition: height 0.5s;
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
    font-family:Roboto;
}

#input{
    height:40px;
    border-color:#6CB2B2;
    border-top-left-radius: 7px;
    border-bottom-left-radius: 7px;
    font-size:20px;
    font-family: Ubuntu;
    outline:none;
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
