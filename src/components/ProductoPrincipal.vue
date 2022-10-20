<template>

    <div class="row">
        <h3>{{dats_producto.nombre}}</h3>
    </div>
    <div class="row">
        <div class="col-12 col-sm-6 col-md-4 ">
            <img :src="dats_producto.imagen" alt="" style="width: 100%;">
        </div>
        <div class="col-12 col-sm-6  col-md-8">
            <h6 v-html="dats_producto.descripcion"></h6>
            <div class="p-3 mb-2 text-white" :style="precioEstilos">
                Precio: {{dats_producto.precio}} BOB
            </div>
            <h5>Color</h5>
            <div>

                <div class="color-box clic" v-for="color in dats_producto.colores" :key="color"
                    :style="{background: [color]}" v-on:click="seleccionarColor(color)"></div>
            </div>
            <h5>Cantidad</h5>
            <div class="quantity">
                <button v-on:click="disminuirCantidad()">-</button>
                <div>{{cantidad_elegido}}</div>
                <button v-on:click="aumentarCantidad()">+</button>
            </div>
            <div class="buy-box">
                <button type="button" class="btn btn-primary" v-on:click="comprar()"
                    :disabled="cantidad_elegido == 0 || color_elegido == null ? true :false">Comprar</button>
            </div>

        </div>
    </div>

</template>

<script>
export default {
    name: 'ProductoPrincipal',
    data() {
        return {
            producto: {
                id: 1,
                imagen: "https://ae01.alicdn.com/kf/Sc3cc58f2a441419f970cc01f9e5358fbw/Dron-LU3-MAX-GPS-8K - HD - profesional - con - c - mara - Dual - card - n - autoestabilizador - Motor - sin.jpg_Q90.jpg_.webp",
                nombre: "Dron LU3 MAX GPS 8K HD",
                descripcion: "Dron LU3 MAX GPS 8K HD profesional con <b>cámara Dual</b>,cardán autoestabilizador,Motor sin escobillas para evitar obstáculos,cuadricóptero plegable ",
                precio: "620",
                colores: ["red", "blue", "black", "yellow"]
            },
            precioEstilos: "background: orangered; color: white; font-weight: bold",
            cantidad_elegido: 1,
            color_elegido: null,
            pedido: {
                id: null,
                cantidad: 1,
                color: ''
            },
            dats_producto:[]
        }
    },
    methods: {
        seleccionarColor: function (color) {
            this.precioEstilos =  "background:"+color+"; color: white; font-weight: bold",
            this.color_elegido = color;
        },
        disminuirCantidad: function () {
            if (this.cantidad_elegido == 1) {
                this.cantidad_elegido = 1;
            } else {
                this.cantidad_elegido = this.cantidad_elegido - 1;
            }
        },
        aumentarCantidad: function () {
            this.cantidad_elegido = parseFloat(this.cantidad_elegido + 1);
        },
        comprar: function () {


            if (this.cantidad_elegido == 1) {
                if (this.color_elegido == '') {
                    alert('Eliga un color primero');
                } else {
                    alert('Eligio el color: ' + this.color_elegido);
                }
            } else {
                if (this.color_elegido == '') {
                    alert('Eliga un color primero');
                } else {
                    this.pedido.id = this.dats_producto.id;
                    this.pedido.cantidad = this.cantidad_elegido;
                    this.pedido.color = this.color_elegido;


                    alert(JSON.stringify(this.pedido));
                }
            }


        },
        verDatosProducto: function (producto) {
            this.cantidad_elegido    = 1;
            this.color_elegido      = '';
            this.pedido         = {
                id: null,
                cantidad: 1,
                color: ''
            }
            this.dats_producto = JSON.parse(producto);
        }
    }
}
</script>
