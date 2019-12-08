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
                <th>Email</th>
                <th>Created At</th>
            </thead>
            <tbody>
                <tr v-for="user in users" :key="user.id">
                    <td>{{ user.id }}</td>
                    <td>{{ user.name }}</td>
                    <td>{{ user.email }}</td>
                    <td>{{ user.created_at }}</td>
                </tr>
            </tbody>
        </table>
    </div>
</template>
<script>
export default {
    mounted() {
        console.log("Hello World");
        axios.post('api/index', {}).then(response => {
            this.users = response.data;
        });
    },

    data: function() {
        return {
            users: null,
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