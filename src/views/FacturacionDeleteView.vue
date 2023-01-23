<template >
    <div class="container">
        <b-form-input v-model="text" placeholder="Enter your name"></b-form-input>
        <div class="mt-2">Value: {{ text }}</div>
        <b-button  v-on:click="eliminarFactura()" variant="danger">Eliminar </b-button>
    </div>
</template>

<script>
export default {
    data() {
        return {
            text: ''
        }
    },
    methods: {
        eliminarFactura() {
           this.axios.delete(`http://localhost:8084/facturacionWS/api/facturacion/${this.text}`).then(()=>{
             alert(`Factura #${this.text} eliminada`)
            });
        }

    }
}
</script>