<template>
  <div class="w-100 d-flex">
    <div class="w-50 d-flex justify-content-start">
      <img v-bind:class="{search:!pesquisa, nosearch:pesquisa}" id="logo" class="nosearch mt-3 ml-5" src="@/assets/Logo_CPI.svg"/>
    </div>
    <div class="w-50 d-flex justify-content-end mt-5">
      <button v-bind:class="{btn_pesquisa:pesquisa, btn_nopesquisa:!pesquisa}" id="b_lo" class="btn">Login</button> 
      <button v-bind:class="{btn_pesquisa:pesquisa, btn_nopesquisa:!pesquisa}" id="b_ca" class="btn ml-3 mr-5 text-white">Cadastro</button> 
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Vue, Prop} from 'vue-property-decorator';

@Component
export default class Nav extends Vue {
  @Prop() pesquisa!: boolean
}
</script>

<style scoped>
.nosearch{
  transition: max-width 0.7s;
  overflow: hidden;
  max-width: 180px;
}

.search{
  transition: max-width 0.7s;
  overflow: hidden;
  max-width: 100px;
}

.btn_nopesquisa{
  outline:none;
  transition: max-width 0.7s;
  transition: height 0.7s;
  overflow: hidden;
  font-size: 18px;
  font-family: Ubuntu;
  height:40px;
  max-width:110px;
}


.btn_pesquisa{
  outline:none;
  transition: max-width 0.7s;
  transition: height 0.7s;
  overflow: hidden;
  font-size: 21px;
  font-family: Ubuntu;
  height:50px;
  max-width:120px;
}

#b_ca{
  background-color:#6CB2B2;
}

</style>
