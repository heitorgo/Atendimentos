<template>
    <main class="main" id="main">
        <div class="container">
            <h1 class="title">Cadastrar Cliente</h1>
            <form class="row g-3">
                <div class="col-md-6">
                    <label for="nome_cliente" class="form-label">Nome:</label>
                    <v-text-field type="text" id="nome_cliente" outlined dense spellcheck="false"
                    v-model="nome" max-length="255" :rules="[rules.required, rules.nome]"></v-text-field>
                </div>
                <div class="col-md-6">
                    <label for="telefone_cliente" class="form-label">Telefone:</label>
                    <v-text-field type="text" v-model="telefone" maxlength="14" v-mask='telefoneMask'  
                    autocomplete="off" :rules="[rules.telefone]" dense outlined></v-text-field>
                </div>
                <div class="col-md-6">
                    <label for="nome_fantasia" class="form-label">Nome Fantasia:</label>
                    <v-text-field type="text" id="fantasia_cliente" outlined dense v-model="fantasia" maxlength="255" spellcheck="false"
                    :rules="[rules.required, rules.nome]" autocomplete="off"></v-text-field>
                </div>
                <div class="col-md-6">
                    <label for="cnpj" class="form-label">CNPJ:</label>
                    <v-text-field type="text" outlined dense v-model="cnpj" maxlength="18" id="cnpj_cliente" name="cpfcnpj"
                    :rules="[rules.cnpj]" onkeypress="mascaraMutuario(this,cpfCnpj)"  onblur='clearTimeout()' autocomplete="off"></v-text-field>
                </div>
                <div class="col-md-12">
                    <label for="contato" class="form-label">Contato:</label>
                    <v-text-field required type="text" maxlength="255" name='contato' id="contato" 
                    dense outlined autocomplete="off"></v-text-field>
                </div>
                <div class="col-md-6">
                    <div class="form-check form-check-inline">
                        <input class="form-check-input" type="radio" name="inlineRadioOptions" id="inlineRadio1" value="1" @click="ativo = true" checked/>
                        <label class="form-check-label" for="inlineRadio1">Ativo</label>
                    </div>
                    <div class="form-check form-check-inline">
                        <input class="form-check-input" type="radio" name="inlineRadioOptions" id="inlineRadio2" value="0" @click="ativo = false"/>
                        <label class="form-check-label" for="inlineRadio2">Inativo</label>
                    </div>
                </div>
                <div class="col-12 mt-5">
                    <button class="btn btn-red" :disabled="noNome || noFantasia || shortNome || shortCnpj ||
                    shortTelefone || shortFantasia">Cadastrar Cliente</button>
                    <router-link to="/clientes/">
                        <a class="btn btn-dark ml-2"> Voltar </a>
                    </router-link>
                </div>
            </form>
        </div>
    </main>
</template>

<script>
export default {
    data(){
        return{
            nome: '',
            telefone: '',
            fantasia: '',
            cnpj: '',
            ativo: null
        }
    },
    computed:{
        telefoneMask(){
            return this.$store.getters.telefoneMask
        },
        shortCnpj(){
            if(this.cnpj.length > 0){
                return this.cnpj.length < 14
            }else{
                return this.cnpj.length > 0
            }
        },
        noNome(){
            return this.nome == ''
        },
        shortNome(){
            return this.nome.length < 3
        },
        shortTelefone(){
            if(this.telefone.length > 0){
                return this.telefone.length < 14
            }else{
                return this.telefone.length > 0
            }
            
        },
        noFantasia(){
            return this.fantasia == ''
        },
        shortFantasia(){
            if(this.fantasia.length > 0){
                return this.fantasia.length < 3
            }else{
                return this.fantasia.length > 0
            }
        },
        rules(){
            return this.$store.getters.rules
        }
    },
    beforeRouteLeave(to, from, next){
        if(this.nome == '' && this.telefone == '' && this.fantasia == '' && this.cnpj == ''){
            next()
        }else{
            if(confirm('Seus dados serão perdidos, tem certeza disso ?')){
                next()
            }else{
                next(false)
            }
        }
    }
}
</script>