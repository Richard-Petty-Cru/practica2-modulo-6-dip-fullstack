<template>

    <div class="col" v-for="producto in productosRelacionados" :key="producto" v-on:click="detalleProducto(producto)">
        <div class="card" style="width: 18rem;">
            <div class="card-body">
                <h5 class="card-title">{{producto.nombre}}</h5>
                <img :src="producto.imagen" alt="" style="width: 100%;" >
                <p class="card-text">{{producto.descripcion}}</p>
                <div class="producto-relacionado-precio">Precio: {{producto.precio}} BOB</div>
                <div>
                    <div>
                        <div class="color-box" v-for="color in producto.colores" :key="color" :style="{background: [color]}"></div>

                    </div>
                </div>
            </div>
        </div>
    </div>


</template>

<script>
import axios from 'axios'
export default {
    name: 'ProductoRelacionado',
    data() {
        return {
            productosRelacionados:[],
            dats_producto:[]
        }
    },
    created: function () {
        this.getProductosRelacionados();
     
    },
    methods: {
        getProductosRelacionados: function () {
            axios.get('http://localhost:3333/persona').then(response =>{
                this.productosRelacionados = response.data;
                this.detalleProducto(this.productosRelacionados[0]);
            });
        },
        detalleProducto: function(producto) {
            this.dats_producto  = producto;
            this.$emit('detalleProducto', JSON.stringify(this.dats_producto));
        }
    },
    
}
</script>