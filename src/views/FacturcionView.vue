<template>
  <div class="container">
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
  created() {
    this.verFactura();
  },
  methods: {
    verFactura() {

      const api = "http://localhost:8084/facturacionWS/api/facturacion/list";
      this.axios.get(api).then((response) => {
        response.data.forEach(element => {
          let factura = {
            id: element.numerofactura,
            nombre: element.nombreCliente,
            iva: element.iva,
            subtotal: element.subTotal,
            total: element.total
          }
          this.facturas.push(factura);
        });
      })
    },

  }
}



</script>