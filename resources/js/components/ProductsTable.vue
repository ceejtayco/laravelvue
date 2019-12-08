<template>
    <div>
        <div id="add-product-button">
            <button type="button" class="btn btn-danger" data-toggle="modal" data-target="#modalProduct">
                Add Product
            </button>
        </div>

        <table class="table">
            <thead>
                <th>ID</th>
                <th>Name</th>
                <th>Description</th>
                <th>Price</th>
                <th>Qty</th>
            </thead>
            <tbody>
                <tr v-for="product in products" :key="product.id">
                    <td>{{ product.id }}</td>
                    <td>{{ product.name }}</td>
                    <td>{{ product.description }}</td>
                    <td> {{ product.price }} </td>
                    <td> {{ product.qty }} </td>
                </tr>
            </tbody>
        </table>
    </div>
</template>
<script>
export default {
    mounted() {
        axios.post('api/products', {}).then(response => {
            this.products = response.data;
        });
    },

    data: function() {
        return {
            products: null,
        }
    },

    props: [
        // 'key'
    ]

}
</script>
<style>
    .table th {
        text-align: center;
    }
    #add-product-button {
        padding-bottom: 10px;
    }
  
</style>