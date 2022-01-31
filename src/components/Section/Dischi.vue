<template>
  <div class="container">
    <div v-if="!loading" class="dischi">
      <Disco v-for="(elemento, indice) in arrayDischi" :key="indice" :disco="elemento" />
    </div>
    <Loader v-else />
  </div>
</template>

<script>
import axios from "axios";
import Disco from "../Commons/Disco.vue";
import Loader from "../Commons/Loader.vue";

export default {
  name: "Dischi",
  data() {
    return {
      apiURL: "https://flynn.boolean.careers/exercises/api/array/music",
      arrayDischi: [],
      loading: true,
    };
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
            this.loading = false;
          })
          .catch(function (error) {
            // handle error
            console.log(error);
          });
      }, 1000);
    },
  },
  components: {
    Disco,
    Loader,
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
