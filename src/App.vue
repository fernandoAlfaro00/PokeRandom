<template>
  <div id="app">
    <center>
      <h1>{{ name }}</h1>
      <div
        class="container-img tamanio pointer"
        @click.prevent="reproducirSonido(sonido)"
      >
        <img alt="" :src="sprite" :srcset="(sprite, sprite2)" />
        <div class="container-btn sonido">
          <div class="icon">
            <i class="fas fa-volume-up"></i>
          </div>
        </div>
      </div>

      <div class="info">
        <component-types :tipos="tipos"></component-types>
        <p>Peso: {{ peso }}Kg</p>
      </div>

      <div id="barraSuperior">
        <component-button class="red" v-if="automatico" @click="pararBusqueda">
          Siguiente en {{ contador }}/5
        </component-button>
        <component-button class="green" v-else @click="busquedaAutomatica">
          Azar Automatico
        </component-button>
      </div>
    </center>
    <component-button
      class="blue"
      @keyup.enter="getNewPokemon"
      @click="getNewPokemon"
    >
      Buscar
    </component-button>
  </div>
</template>

<script>
import axios from "axios";
import componentTypes from "./component/Types.vue";
import componentButton from "./component/Button.vue";

export default {
  name: "app",
  components: {
    componentTypes, componentButton
  },
  data() {
    return {
      search: "",
      name: "",
      sprite: "",
      sprite2: "",
      peso: "",
      tipos: "",
      automatico: false,
      contador: 0,
      sonido: ""
    };
  },
  methods: {
    getRandomInt() {
      return Math.floor(Math.random() * (899 - 1)) + 1;
    },

    getNewPokemon() {
      axios
        .get("https://pokeapi.co/api/v2/pokemon/" + this.getRandomInt())
        .then((response) => {
          (this.name = response.data.name),
            (this.sprite =
              response.data.sprites.other["official-artwork"].front_default);
          this.sprite2 = response.data.sprites.other.dream_world.front_default;
          this.peso = response.data.weight;
          this.tipos = response.data.types;
          this.sonido =
            "https://veekun.com/dex/media/pokemon/cries/" +
            response.data.id +
            ".ogg";
        }).catch(
          (error) => {

            console.log("El error",error)
          }
        );
    },
    busquedaAutomatica() {
      const self = this;
      this.automatico = !this.automatico;

      this.interval = setInterval(function () {
        // setInterval(() => {

        // }, 1000);

        self.contador += 1;
        if (self.contador === 6) {
          self.getNewPokemon();
          self.contador = 0;
        }
      }, 1000);

      console.log(this.interval);
    },
    pararBusqueda() {
      this.automatico = !this.automatico;
      clearInterval(this.interval);
    },
    reproducirSonido(sonido) {
      if (sonido) {
        let audio = new Audio(sonido);

        audio.play();
      }
    },
  },
  mounted() {
    this.getNewPokemon();
  },
};
</script>

<style>
@import url("https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.15.2/css/all.min.css");
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h1,
h2 {
  font-weight: normal;
}



.btn_tamanio {
  width: 170px;
  height: 60px;
  font-size: 20px;
}

.tamanio {
  width: 300px;
  border: gray solid 2px;
  border-radius: 10%;
}

.tamanio img {
  width: 100%;
}

.icon {
  background-color: white;
  color: black;
  padding: 3px 6px;
  margin: 4px 4px;
  font-size: 24px;
}

.pointer {
  cursor: pointer;
}


</style>
