<template>
    <!-- Modal -->
    <div class="modal fade" id="modalProduct" tabindex="-1" role="dialog" aria-labelledby="exampleModalLabel" aria-hidden="true">
    <div class="modal-dialog" role="document">
        <div class="modal-content">
        <div class="modal-header">
            <h5 class="modal-title" id="exampleModalLabel">Add Product</h5>
            <button type="button" class="close" data-dismiss="modal" aria-label="Close">
            <span aria-hidden="true">&times;</span>
            </button>
        </div>
        <div class="modal-body">
            <div v-if="success">
                <div class="alert alert-success" role="alert">
                    <p v-text="message"></p>
                </div>
            </div>
            <form @submit.prevent="submit">
                <div class="form-group">
                    <div class="row">
                        <div class="col-md-2">
                            <label for="">Name</label>
                        </div>
                        <div class="col-md-10">
                            <input type="text" name="name" id="name" class="form-control" placeholder="Product Name" v-model="name">
                        </div>
                    </div>
                </div>
                <div class="form-group">
                    <div class="row">
                        <div class="col-md-2">
                            <label for="">Description</label>
                        </div>
                        <div class="col-md-10">
                            <input type="text" name="description" id="description" class="form-control" placeholder="Product Description" v-model="description">
                        </div>
                    </div>
                </div>
                <div class="form-group">
                    <div class="row">
                        <div class="col-md-2">
                            <label for="">Price</label>
                        </div>
                        <div class="col-md-10">
                            <input type="text" name="price" id="price" class="form-control" placeholder="Product Price" v-model="price">
                        </div>
                    </div>
                </div>
                <div class="form-group">
                    <div class="row">
                        <div class="col-md-2">
                            <label for="">Qty</label>
                        </div>
                        <div class="col-md-10">
                            <input type="text" name="qty" id="qty" class="form-control" placeholder="Product Quantity" v-model="qty">
                        </div>
                    </div>
                </div>
                <div class="form-group text-center">
                    <button class="btn btn-danger btn-add-product">Add Product</button>
                </div>
                
            </form>
        </div>
        
        </div>
    </div>
    </div>
</template>
<script>
export default {
    mounted() {
        console.log("mounted");
    },
    data: function() {
        return {
            name: '',
            description: '',
            price: '',
            qty: '',
            success: false
        }
    },
    methods: {
        submit() {
            axios.post('api/add-product', {
                name: this.name,
                description: this.description,
                price: this.price,
                qty: this.qty
            }).then(response => {
                this.message = response.data.message;
                this.name = '';
                this.description = '';
                this.price = '';
                this.qty = '';
                this.success = true;
            });
        }
    },
}
</script>
<style>
    .btn-add-product {
        display: block;
        width: 100%;
        margin: auto;
        padding: auto;
    }

    label {
        padding-top: 5px;
    }

    .alert-success {
        padding-bottom: 4px;
    }
</style>
