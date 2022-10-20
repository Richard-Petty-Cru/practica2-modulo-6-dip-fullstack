<template>
  <NavBar></NavBar>
  <div class="container">
    <ProductoPrincipal ref="mostrarDetalleProducto"></ProductoPrincipal>
  </div>

  <div class="container ">
    <div class="row">
      <h4>Productos relacionados</h4>
    </div>
    <div class="row">
      <ProductoRelacionado 
      @detalleProducto="detalleProducto"
      
      ></ProductoRelacionado>
    </div>
  </div>

  <FooterTemplate></FooterTemplate>

</template>


<script>
import NavBar from './components/NavBar.vue';
import ProductoPrincipal from './components/ProductoPrincipal.vue';
import ProductoRelacionado from './components/ProductoRelacionado.vue';
import FooterTemplate from './components/FooterTemplate.vue';


export default {
  name: 'App',
  components: {
    NavBar,
    ProductoPrincipal,
    ProductoRelacionado,
    FooterTemplate
  },
  methods: {
    detalleProducto (producto) {
    
      this.$refs.mostrarDetalleProducto.verDatosProducto(producto);

    }
  }
}
</script>



<style>
.color-box {
  width: 40px;
  height: 40px;
  border-radius: 50%;
  margin: 7px;
  display: inline-block;
}

.clic {
  cursor: pointer;
}

.quantity button {
  border-radius: 50%;
  display: inline-block;
  width: 30px;
}

.quantity div {
  text-align: center;
  min-width: 30px;
  display: inline-block;
  font-weight: bold;
}

.buy-box {
  margin: 20px;
}

footer {

  text-align: center;
  padding: 30px 10px;
  margin-top: 50px;
  min-height: 100px;
}

.container {
  margin-top: 50px;
}

.producto-relacionado-precio {
  background: orangered;
  color: white;
  text-align: center;
  padding: 10px;
}
</style>