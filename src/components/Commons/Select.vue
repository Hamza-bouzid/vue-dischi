<template>
  <div class="select">
    <select @change="cambiaSelect">
      <option >--</option>
      <option value="all">All</option>
      <option value="rock">Rock</option>
      <option value="pop">Pop</option>
      <option value="jazz">Jazz</option>
      <option value="metal">Metal</option>
    </select>
  </div>
</template>

<script>
export default {
  name: "Select",

  data() {
    return {
      genere: "",
    };
  },

  methods: {
    cambiaSelect: function (e) {
      this.genere = e.target.value
      this.$emit('filtra', this.genere)
    },
  },
};
</script>

<style lang="scss" scoped>
.select {
  display: flex;
  justify-content: center;
  align-items: center;
  select {
    width: 50%;
    padding: 5px 10px;
    border-radius: 20px;
    border: none;
    font-size: 20px;
    outline: none;
    background-color: #2e3a46;
    color: #fff;
  }
}
</style>
