<template>
    <div class="card">
        <h3>{{ name }} - {{ code }}</h3>
        <address>
            <strong>Endereço: {{ address }}</strong>
            <p>Cidade: {{ city }}</p>
            <p>Área total: {{ area }} m²</p>
        </address>
    </div>
</template>

<script>

export default {
    name: 'Warehouse',
    props: {
        id: Number,
        name: String,
        code: String,
        address: String,
        city: String,
        area: Number
    }
}

</script>

<style>

.card {
    border-style: solid;
    border-radius: 25px;
    margin: 0 auto 10px auto;
    width: 30%;
}
</style>