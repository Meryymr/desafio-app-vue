<template>
  <div id="app">
    <div class="container">
      <div class="row">
        <h1 class="text-center py-2">Modifica tu texto junto a Vue</h1>
        <div id="colorFondoDoc" class="col-6 py-5 text-white ">
          <form class="d-flex flex-column">
            <!-- Cambio de fondo -->
            <label for="">Color de fondo</label>
            <input type="texto" id="colorFondo" name="colorFondo"
              v-model="colorFondo" placeholder="Escribe un color en Inglés">
            <br>
            <!-- Cambio color de texto -->
            <label for="">Color de texto</label>
            <input type="color" id="colorTexto" name="colorTexto"
              v-model="colorTexto" placeholder="Escribe un color en Inglés">
            <br>
            <div>
              <label for="" class="pe-2">Mostrar texto</label>
              <input type="checkbox" id="mostrarTexto" name="mostrarTexto"
                v-model="mostrarTexto">
            </div>
            <br>
            <!-- Cambio rango de borde -->
            <div>
              <label for="">Borde</label><br>
              <input type="range" id="borde" name="borde" min="0" max="50"
                step="1" v-model="borde"> <span>{{ borde + "%" }}</span>
            </div>
            <br>
            <!-- Text area para contenido -->
            <div>
              <label for="">Contenido textual</label><br>
              <div class="d-flex row container">
                <textarea name="text" id="contenidoTextual"
                  placeholder="Escribe el texto que quieres mostrar" rows="3"
                  cols="50%" v-model="contenidoTextual"></textarea>
              </div>
            </div>
            <!-- Opciones para tipografía -->
            <div>
              <label for="tipografias">Tipografías</label>
              <br>
              <select name="tipografias" id="tipografias" v-model="tipografias">
                <option :value="tipografia"
                  v-for="(tipografia, index) in tipografiasArray" :key="index">
                  {{ tipografia }}</option>
              </select>
            </div>
            <!-- Checkbox opaco -->
            <div class="py-3">
              <label for="">Opacidad</label><br>
              <input type="range" min="0" max="1" step="0.1" v-model="opaco"
                id="opaco">
            </div>
            <!-- Seleccion de tamaño de letra -->
            <div>
              <label for="">Tamaño Letra</label>
              <div class="row">
                <div class="col-4"> <input type="radio" id="pequeño"
                    name="fav_language" value="smallText" v-model="tamanoLetra">
                  <label for="pequeño">Pequeño</label><br>
                </div>
                <div class="col-4"> <input type="radio" id="mediano"
                    name="fav_language" value="mediumText"
                    v-model="tamanoLetra">
                  <label for="mediano">Mediano</label><br>
                </div>
                <div class="col-4"> <input type="radio" id="grande"
                    name="fav_language" value="largeText" v-model="tamanoLetra">
                  <label for="grande">Grande</label>
                </div>
              </div>
            </div>

          </form>
        </div>

        <div
          class="container-resultado col-6 container py-5 d-flex align-items-center justify-content-center">
          <div id="cuadrado"
            class="h-75 w-75 d-flex align-items-center justify-content-center"
            :style="{
              borderRadius: borde + '%',
              backgroundColor: colorFondo,
              fontWeight: tipografias,
              opacity: opaco
            }">
            <p :style="{ color: colorTexto }"
              :class="[tamanoLetra == 'largeText' ? largeClass : tamanoLetra == 'smallText' ? smallClass : mediumClass]"
              v-show="mostrarTexto">
              {{ contenidoTextual }}</p>
          </div>
        </div>
      </div>
    </div>

  </div>
</template>
<script>


export default {
  name: 'App',
  components: {
  },
  data() {
    return {
      colorFondo: "",
      colorTexto: "",
      mostrarTexto: true,
      borde: 0,
      contenidoTextual: "",
      tipografias: "normal",
      opaco: 1,
      tamanoLetra: "mediumText",
      tipografiasArray: [
        "bold", "normal", "lighter"
      ],
      smallClass: "smallText",
      mediumClass: "mediumText",
      largeClass: "largeText"

    }
  }

}
</script>

<style>
* {
  font-family: "Poppins", sans-serif;
}

#colorFondoDoc {
  background-color: rgb(0, 125, 90);
  border: 3px solid rgb(3, 60, 41);
}

.smallText {
  font-size: 14px;
}

.mediumText {
  font-size: 24px;
}

.largeText {
  font-size: 34px;
}
</style>
