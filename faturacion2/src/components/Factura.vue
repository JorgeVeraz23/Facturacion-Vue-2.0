<template>
    <div>
        <h1>Factura </h1>
        <p>Fecha: </p>
        <h2>Detalles</h2>
        <table>
            <thead>
                <tr>
                    <th>Producto</th>
                    <th>Precio</th>
                    <th>Cantidad</th>
                </tr>
            </thead>
            <tbody>
                <tr>
                    <td> </td>
                    <td> </td>
                    <td>  </td>
                </tr>
            </tbody>
        </table>
    </div>
</template>

<script>
import axios from "axios";

    export default {
        data(){
            return {
                facturas: [],
                facturaCabecera: {
                    idFacturaCabecera: null,
                    numeroFactura: '',
                    fecha: '',
                    facturasDetalle: [
                        {
                            producto: '',
                            precio: 0,
                            cantidad: 1
                        }
                    ]
                },
                loading: false,
            };
        },
        methods: {
            getAllFacturas(){
                this.loading= true;
                 axios.get("https://localhost:7056/api/Factura/ObtenerTodasLasFacturaConDetalles").then(response => {
                    console.log(response);
                    this.facturas = response.data;
                    this.loading = false;
                 }).catch(() => this.loading = false);
            }
        },
        created: function(){
            this.getAllFacturas();
        }
    }
</script>

<style lang="scss" scoped>

</style>