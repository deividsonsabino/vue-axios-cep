<template>
    <div>
        <h1 v-text="title"></h1>

        <form @submit.prevent="onSubmit"> 
            <div :class="{'has-error': error}">
                <input type="text" placeholder="CEP" v-model="cep">
                <button type="submit">Buscar</button>
                <div v-if="error" v-text="error"></div>
            </div>

        </form>
        <div v-if="preloader">

            <img src="../assets/preloader.gif" alt="carregando">

        </div>
        <div v-if="address.cep">
            <p><b>Cidade: </b> {{address.localidade}}</p>
            <p><b>Bairro: </b> {{address.bairro}}</p>
            <p><b>Logradouro: </b> {{address.logradouro}}</p>
        </div>


    </div>
</template>

<script>
import axios from 'axios'

export default {
    data () {
        return {
            title: 'Busca CEP',
            cep: '',
            address: {},
            preloader: false,
            error: ''
        }
    },
    methods: {
        onSubmit() {
            this.reset()
            this.preloader = true
            axios.get(`https://viacep.com.br/ws/${this.cep}/json/`)
                .then(response => {
                    console.log(response)

                    if (response.data.erro)
                        this.error = 'Cep Inválido!'
                    else
                        this.address = response.data
                })
                .catch(error => {
                    console.log(error)
                    this.error = '404'
                })
                .finally(() => this.preloader = false)
        }, 
        reset() {
            this.error = '',
            this.address = {}
        }
    }
}
</script>

<style scoped>
.has-error{color: red;}
.has-error input{border:1px solid red;}
</style>