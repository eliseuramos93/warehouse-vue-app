<template>
    <div>
        <h1>Galpões Cadastrados</h1>

        <input class="form" v-model="term" type="text" placeholder="Buscar galpão">

        <div v-for="w in filterWarehouse" :key="w.id">
            <Warehouse
                :name = "w.name"
                :code = "w.code"
                :address = "w.address"
                :city = "w.city"
                :area = "w.area"
            />
        </div>
    </div>
</template>

<script>
import Warehouse from '../components/Warehouse.vue';

export default {
    name: 'WarehouseList',

    components: {
        Warehouse
    },

    data(){
        return{
            warehouses: [],
            term: '',
        }
    },

    methods: {
        async getWarehouses(){
            // realizando a requisição
            const response = await this.$http.get('http://localhost:3000/api/v1/warehouses');

            const result = await response.json();

            // exibindo os dados no console do navegador
            // console.log(result);

            // adicionando os dados de result no array warehouses
            this.warehouses = result;
            return this.warehouses;
        }
    },

    computed: {
        filterWarehouse(){
            return this.warehouses.filter(warehouse => {
                return warehouse.name.toLowerCase().includes(this.term.toLowerCase());
            })
        }
    },

    async mounted(){
        this.getWarehouses();
    }
}
</script>

<style>
    .form {
        margin: 0 0 20px 0;
    }
</style>