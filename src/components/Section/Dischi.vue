<template>
  <div class="container">
    <Select @filtra="filtraDischi" />
    <div v-if="!loading">
      <div class="dischi">
        <Disco v-for="(elemento, indice) in dischiFiltrati" :key="indice" :disco="elemento" />
      </div>
    </div>
    <Loader v-else />
  </div>
</template>

<script>
import axios from "axios";
import Disco from "../Commons/Disco.vue";
import Loader from "../Commons/Loader.vue";
import Select from "../Commons/Select.vue";

export default {
  name: "Dischi",

  components: {
    Disco,
    Loader,
    Select,
  },

  data() {
    return {
      apiURL: "https://flynn.boolean.careers/exercises/api/array/music",
      arrayDischi: [],
      loading: true,
      options: "",
    };
  },

  computed: {
    dischiFiltrati() {
      return this.arrayDischi.filter((elemento) => {
        if (elemento.genre.toLowerCase() === this.options) {
          return elemento.genre;
        } else if (this.options == "all") {
          return elemento.genre;
        }
      });
    },
  },

  created() {
    this.getDischi();
  },

  methods: {
    getDischi: function () {
      setTimeout(() => {
        axios
          .get(this.apiURL)
          .then((risposta) => {
            // handle success
            this.arrayDischi = risposta.data.response;
            this.dischiFiltrati = risposta.data.response;
            this.loading = false;
          })
          .catch(function (error) {
            // handle error
            console.log(error);
          });
      }, 1000);
    },

    filtraDischi: function (input) {
      this.options = input;
    },
  },
};
</script>

<style lang="scss" scoped>
.container {
  margin-top: 40px;
}
.dischi {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-wrap: wrap;
}
</style>
