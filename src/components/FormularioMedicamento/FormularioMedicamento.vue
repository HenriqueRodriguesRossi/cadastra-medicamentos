<template>
    <h3>Formulário de Cadastro de medicamentos</h3> <br>

    <form class="form" @submit.prevent="submitForm">
        <div>
            <label for="nome">Nome:</label> <br>
            <input type="text" placeholder="Informe o nome do medicamento" class="inputs nome" v-model="medicamento">
        </div>
        <div>
            <label for="laboratorio">Laboratório</label> <br>
            <input type="text" class="inputs laboratorio" placeholder="Informe o nome do laboratório" v-model="laboratorio">
        </div>
        <div>
            <label for="preco">Preço</label> <br>
            <input type="number" class="inputs preco" placeholder="Informe o preço" v-model="preco">
        </div>

        <button class="cadastrar" type="submit">Cadastrar</button>
    </form>
</template>

<script>
export default {
    emits: ['submit'],
    data(){
        return{
            medicamento: "",
            laboratorio: "",
            preco: 0,
        }
    },
    methods:{
        submitForm() {
            // Emitir o evento 'submit' com os dados do formulário
            this.$emit('submit', this.medicamento, this.laboratorio, this.preco);
        }
    }
}
</script>

<style scoped>
.container {
    width: 100%;
    height: auto;
    padding: 9px, 16px, 9px, 16px;
}

h3 {
    margin-top: 42px;
    font-size: 25px;
    font-weight: 900;
    line-height: 31px;
    margin-left: 11px;
}

.form {
    width: auto;
    height: auto;
    display: flex;
    justify-content: space-around;
    align-items: center;
}

.form label {
    padding-left: 10px;
}

.form .inputs {
    width: 342px;
    height: 40px;
    border: 2px solid black;
    border-radius: 2px;
}

button {
    width: 224px;
    height: 38px;
    background-color: #525252;
    color: #FFFFFF;
    border: none;
    cursor: pointer;
    padding: 9px, 16px, 9px, 16px;
    border-radius: 2px;
} 
</style>