<template>
  <div class="loader">
    <div class="lds-dual-ring"></div>
  </div>
</template>

<script>
export default {
  name: "Loader",
};
</script>

<style lang="scss" scoped>
.loader {
  position: fixed;
  top: 0;
  left: 0;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  width: 100%;
  height: 100%;
  background: #000;
}

.lds-dual-ring {
  display: inline-block;
  width: 80px;
  height: 80px;

  &::after {
    content: " ";
    display: block;
    width: 64px;
    height: 64px;
    margin: 8px;
    border-radius: 50%;
    border: 6px solid #1ed760;
    border-color: #1ed760 transparent #1ed760 transparent;
    animation: lds-dual-ring 1.2s linear infinite;
  }
}

@keyframes lds-dual-ring {
  0% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(360deg);
  }
}
</style>
