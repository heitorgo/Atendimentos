<template>
    <div class="container pa-0">
            <nav class="navbar navbar-expand-lg navbar-light">
                <router-link class="navbar-brand" to="/atendimentos">
                    <img src="../../../assets/imgs/logos/logo-hypersoft.svg" width="150" alt="Logo Hypersoft" class="img-fluid"/>
                </router-link>
                <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav"
                aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation" @click="mobileMenu = true">
                    <span class="navbar-toggler-icon"></span>
                </button>
                <div class="navCustom collapse navbar-collapse" id="navbarNav">
                    <ul class="navbar-nav">
                        <li class="nav-item mr-2">
                            <router-link to="/atendimentos/" class="link" active-class="link-active">
                                <div class="bar-list-item">
                                    <v-icon color="red darken-1">mdi-home-outline</v-icon>
                                    <a class="nav-link" aria-current="page">
                                        <router-link to="/atendimentos/" class="link" active-class="link-active">
                                            Atendimentos
                                        </router-link>
                                    </a>
                                </div>
                            </router-link>
                        </li>
                        <li class="nav-item mr-2">
                            <router-link to="/tecnicos" class="link">
                                <div class="bar-list-item">
                                    <v-icon color="red darken-1">mdi-face-agent</v-icon>
                                    <a class="nav-link">
                                        <router-link to="/tecnicos" class="link" active-class="link-active">
                                            Técnico
                                        </router-link>
                                    </a>
                                </div>
                            </router-link>
                        </li>
                        <li class="nav-item mr-2">
                            <router-link to="/clientes" class="link">
                                <div class="bar-list-item">
                                    <v-icon color="red darken-1">mdi-account-group-outline</v-icon>
                                    <a class="nav-link" >
                                        <router-link to="/clientes" class="link" active-class="link-active">
                                            Cliente
                                        </router-link>
                                    </a>
                                </div>
                            </router-link>
                        </li>
                    </ul>
                </div>
            </nav>
        </div>
</template>

<script>
export default{
    computed:{
        mobileMenu:{
            get(){
                return this.$store.getters.mobileMenu
            },
            set(mobileMenu){
                this.$store.commit('setMobileMenu', mobileMenu)
            }
        }
    }
}
</script>