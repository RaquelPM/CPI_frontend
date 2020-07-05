<template>
  <div class="w-100 d-flex">
    <div class="w-50 d-flex justify-content-start">
      <img 
        v-bind:class="{search:!pesquisa, nosearch:pesquisa}"
        id="logo"
        class="nosearch mt-3 ml-5"
        src="@/assets/Logo_CPI.svg"
      />
    </div>
    <div class="w-50 d-flex justify-content-end mt-5">
      <button
        id="b_lo"
        v-bind:class="{btn_pesquisa:pesquisa, btn_nopesquisa:!pesquisa}"
        @click.stop="drawer = !drawer"
        class="btn ubuntu font-weight-bold"
      >
        Login
      </button> 
      <button
        v-bind:class="{btn_pesquisa:pesquisa, btn_nopesquisa:!pesquisa}"
        @click.stop="cadastro = !cadastro"
        id="b_ca"
        class="btn ml-3 mr-5 text-white ubuntu font-weight-bold"
      >
        Cadastro
      </button> 
    </div>

    <v-navigation-drawer
      v-model="drawer"
      absolute
      right
      temporary
    >
      <form class="h-100 w-100 d-flex align-items-center justify-content-center flex-column">
          <h1 class="ubuntu font-weight-bold mb-5" >Login</h1>
          <div class="d-flex w-100">
            <div id="quadrado" class="w-25 ml-2"></div>
            <input required id="user" type="text" placeholder="João.." class="input_form w-100 bord_input pl-2 mr-2 ubuntu"/>
          </div>
          <div class="w-100 px-2">
            <input required type="password" placeholder="senha" class=" input_form_gray ubuntu input_form pl-3 w-100 mt-3"/>
          </div>
          <div class="w-100 px-2 my-3">
            <!-- Custom select -->
            <CustomInput placeholder="Teste" name="Teste" >
              <span class="text-white">></span>
            </CustomInput>
          </div>
          <div class="d-flex w-100 justify-content-end mb-5">
            <a id="link_esqueci" class="ubuntu mt-1 font-weight-bold mr-2 mb-5">Esqueceu a senha?</a>
          </div>
          <button id="button_submit" type="submit" class="btn mt-5 ubuntu text-white btns_sub">Login</button>
      </form>
    </v-navigation-drawer>

    <v-navigation-drawer
      v-model="cadastro"
      absolute
      right
      temporary
    >
      <form class="h-100 w-100 d-flex align-items-center justify-content-center flex-column px-2">
        <h1 class="ubuntu font-weight-bold mb-5">Cadastro</h1>
        <input id="cas_user" type="text" placeholder="Nome de usuário" required class="ubuntu input_form w-100 bord_input pl-2"/>
        <div class="d-flex w-100 mt-3">
          <div id="quadrado" class="w-25"></div>
          <input id="criar_senha" type="password" placeholder="Crie uma senha" required class="w-100 pl-2 bord_input input_form ubuntu" />
        </div>
        <input required type="password" placeholder="Confirme sua senha" class="input_form_gray ubuntu input_form w-100 mt-3 pl-2"/>
        <div class="d-flex w- mb-3">
          <input type="telephone" placeholder="Telefone" class="w-50 mr-2 input_form mt-3 input_form_gray pl-2"/>
          <select class="w-50 input_form input_form_gray mt-3 pl-2 ubuntu" >
            <option value="A">Aluno</option>
            <option value="P">Professor</option>
          </select>
        </div>
        <button id="button_proxi" type="submit" class="btn mt-5 ubuntu text-white btns_sub">Próxima etapa</button>
      </form>
    </v-navigation-drawer>
  </div>
</template>

<script lang="ts">
import { Component, Vue, Prop} from 'vue-property-decorator';
import Inputs from './Input.vue';

@Component({
    components: {
      CustomInput: Inputs
    }
  })

export default class Nav extends Vue {
  @Prop() pesquisa!: boolean

  drawer=false;
  cadastro=false;

}
</script>


<style>

.btns_sub{
  background-color: var(--primary);
  border-radius:6px;
  font-size:19px;
}

#button_proxi{
  width:180px;
  height:50px;
  background-color: var(--primary);
}

#criar_senha{
  border-top-left-radius: 0px;
  border-bottom-left-radius: 0px;
}

.input_form{
  border-radius:5px;
  height:35px;
}

#button_submit{
  width:120px;
  height:45px;
}

#link_esqueci{
  font-size:11px;
  color: #477878;
}

.input_form_gray{
  background-color:#E1E1E1;
  outline:none;
}

#quadrado{
  background-color: var(--primary);
  border-top-left-radius: 5px;
  border-bottom-left-radius: 5px;
}

#user{
    border-top-left-radius: 0px;
    border-bottom-left-radius: 0px;
}

.nosearch{
  transition: max-width 0.4s;
  overflow: hidden;
  max-width: 150px;
}

.search{
  transition: max-width 0.4s;
  overflow: hidden;
  max-width: 100px;
}

.btn_nopesquisa{
  outline:none;
  transition: max-width 0.4s, height 0.4s;
  overflow: hidden;
  font-size: 18px;
  height:40px;
  max-width:110px;
}


.btn_pesquisa{
  outline:none;
  transition: max-width 0.4s, height 0.4s;
  overflow: hidden;
  font-size: 21px;
  height:50px;
  max-width:120px;
}

#b_ca{
  background-color: var(--primary);
}

.ubuntu{
  font-family: Ubuntu
}

.bord_input{
  border-color: var(--primary);
  border-style:solid !important;
  outline:none;
}

</style>
