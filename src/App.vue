<template>
    <Cabecalho />
    <FormularioMedicamento @submit="AdicionarMedicamento" />
    <div class="container">
        <CardMedicamento v-if="!!todosOsMedicamento" v-for="medicamento in todosOsMedicamento" :key="medicamento.id"
            @favoritar="favoritaMed" :nome="medicamento.nome" :laboratorio="medicamento.laboratorio"
            :preco="medicamento.preco" :id="medicamento.id" />
    </div>
</template>

<script>
import Cabecalho from "./components/Cabecalho/Cabecalho.vue"
import CardMedicamento from "./components/CardMedicamento/CardMedicamento.vue";
import { v4 as uuidv4 } from 'uuid';
import FormularioMedicamento from "./components/FormularioMedicamento/FormularioMedicamento.vue"

export default {
    components: {
        Cabecalho,
        FormularioMedicamento,
        CardMedicamento
    },
    data() {
        return {
            id: 0,
            nome: "",
            laboratorio: "",
            preco: 0.0,
            favorito: false,

            inputError: "",

            todosOsMedicamento: []
        }
    },
    methods: {
        AdicionarMedicamento(nome, laboratorio, preco) {
            if (nome == "" || laboratorio == "" || preco == 0) {
                alert("Todos os campos são obrigatórios!")
                return
            }

            const novoMedicamento = {
                id: uuidv4(),
                nome: nome,
                laboratorio: laboratorio,
                preco: preco,
                favorito: false
            }

            this.todosOsMedicamento.push(novoMedicamento)
        },

        favoritaMed(id) {
            this.todosOsMedicamento = this.todosOsMedicamento.map(item => {
                if (item.id === id) {
                    // Altera o estado de favorito
                    item.favorito = !item.favorito;
                }
                return item;
            });
        },

    }
}
</script>

<style scoped>
.container {
    display: flex;
    flex-wrap: wrap;
    widows: 100vw;
    padding: 1em;
}
</style>