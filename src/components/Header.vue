<template>
  <header>
    <div class="logo">
      <img src="../assets/img/logo-small.svg" alt="Logo" />
    </div>
  </header>
</template>

<script>
export default {
  name: "Header",
};
</script>

<style lang="scss" scoped>
header {
  padding: 10px 20px;
  background-color: #2e3a46;
}
.logo {
  width: 40px;
  img {
    width: 100%;
  }
}
</style>
