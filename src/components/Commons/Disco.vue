<template>
  <div class="disco">
    <img :src="disco.poster" />
    <h3>{{ disco.title }}</h3>
    <h4>{{ disco.author }}</h4>
    <h4>{{ disco.year }}</h4>
  </div>
</template>

<script>
export default {
  name: "Disco",
  props: {
    disco: Object,
  },
};
</script>

<style lang="scss" scoped>
.disco {
  background-color: #2e3a46;
  height: 350px;
  width: 200px;
  padding: 15px;
  margin: 10px 20px;
  text-align: center;

  img {
    width: 100%;
    height: 180px;
  }

  h3 {
    color: #fff;
    text-transform: uppercase;
    margin: 15px 0px;
  }

  h4 {
    color: #7c7c7c;
  }
}
</style>
