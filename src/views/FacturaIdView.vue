<template>
    <div class="container">
        <b-form-input v-model="text" placeholder="Enter your name"></b-form-input>
        <div class="mt-2">Value: {{ text }}</div>
        <b-button  v-on:click="verFactura()" variant="danger">Eliminar </b-button>
      <b-table striped hover :items="facturas"></b-table>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        facturas: Array(),
        text: ''
      }
    },
    methods: {
      verFactura() {
  
        const api = `http://localhost:8084/facturacionWS/api/facturacion/factura/${this.text}`;
        this.axios.get(api).then((response) => {
            
            let factura = {
              id: response.data.numerofactura,
              nombre: response.data.nombreCliente,
              iva: response.data.iva,
              subtotal: response.data.subTotal,
              total: response.data.total
            }
            
            this.facturas.push(factura);
        
        })
      },
  
    }
  }
  
  
  
  </script>