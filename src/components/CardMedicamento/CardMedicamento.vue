<template>
    <div class="card_container">
        <span class="material-symbols-outlined" @click="favoritarMed(id)">
            favorite
        </span>
        <span class="material-symbols-outlined" v-if="favorito">
            heart_check
        </span>
        <img src="https://dmvfarma.vtexassets.com/arquivos/ids/196865/caixa-medicamento-2021.png?v=637695586068000000"
            alt="Imagem do medicamento" />
        <div class="med_info">
            <p>Medicamento: {{ nome }}</p>
            <p>Laboratório: {{ laboratorio }}</p>
            <p>Preço: {{ preco }}</p>
        </div>
    </div>
</template>

<script>
export default {
    props: ['nome', 'laboratorio', 'preco', 'favorito', 'id'],
    methods: {
        favoritarMed(id) {
            // Emitir o evento 'favoritar' para o pai com o ID do medicamento
            this.$emit('favoritar', id);
        },
    },
}
</script>

<style scoped>
.card_container {
    width: calc(100%/4 - 2em);
    height: auto;
    margin: 1em;
    background-color: #C4C4C4;
    display: flex;
    flex-direction: column;
    flex-wrap: wrap;
    border-radius: 10px;
    border: 2px solid black;
}

.card_container span {
    text-align: right;
    margin-right: 20px;
    margin-top: 10px;
    margin-bottom: 10px;
    cursor: pointer;
}

.card_container img {
    margin-left: 30%;
    width: 120px;
    margin-bottom: 10px;
}

.card_container .med_info {
    text-align: center;
    margin-top: 5px;
    margin-bottom: 10px;
}
</style>