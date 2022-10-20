<template>

    <nav class="navbar navbar-expand-lg " :style="{ background: [menuColor] }">
        <div class="container-fluid">
            <a class="navbar-brand" href="#">{{marca}}</a>
            <button class="navbar-toggler" type="button" data-bs-toggle="collapse"
                data-bs-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false"
                aria-label="Toggle navigation">
                <span class="navbar-toggler-icon"></span>
            </button>
            <div class="collapse navbar-collapse" id="navbarSupportedContent">
                <ul class="navbar-nav me-auto mb-2 mb-lg-0">
                    <li class="nav-item" v-for="menu in menus" :key="menu">
                        <a class="nav-link" aria-current="page" :href="menu.url">{{menu.etiqueta}}</a>
                    </li>
                </ul>
            </div>
        </div>
    </nav>

</template>

<script>
export default {
    name: 'NavbBar',
    data() {
        return {
            menuColor: 'lightblue',
            menus: [{
                etiqueta: "Inicio",
                url: "?"
            }, {
                etiqueta: "Tienda",
                url: "?"
            }],
            marca: "MegaDron - RICHARD GONI PATTI CRUZ"
        }
    }
}
</script>