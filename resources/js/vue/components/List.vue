<template>
    <div>
        <h1>Listado de Marcas</h1>
    </div>
    <div class="row">
        <div class="col-12">
            <div class="card">
                <div class="card-header">
                    <h4>Marca</h4>
                </div>
                <div class="card-body">
                    <div class="table-responsive">
                        <table class="table table-bordered">
                            <thead>
                                <tr>
                                    <th>ID</th>
                                    <th>MARCA</th>
                                    <th>DESCRIPCION</th>
                                    <th>ACCIONES</th>
                                </tr>
                            </thead>
                            <tbody v-if="brands.length > 0">
                                <tr v-for="(brand,key) in brands" :key="key">
                                    <td>{{ brand.id }}</td>
                                    <td>{{ brand.name }}</td>
                                    <td>{{ brand.description }}</td>
                                    <td></td>
                                </tr>
                            </tbody>
                            <tbody v-else>
                                <tr>
                                    <td colspan="4" align="center">No existen marcas registradas</td>
                                </tr>
                            </tbody>
                        </table>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        data() {
            return {
                brands: [],
            }
        },
        async mounted() {
            this.$axios.get('/api/brand').then((response) => {
                this.brands = response.data
                console.log(this.brands)
            })
        },
    }
</script>