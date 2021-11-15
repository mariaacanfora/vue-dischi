<template>
  <div class="bg-loader d-flex justify-content-center align-items-center">
    <img src="@/assets/img/spotify-logo.png" alt="spotify-logo-loader" />
  </div>
</template>

<script>
export default {
  name: "Loader",
};
</script>

<style lang="scss">
@import "@/styles/variables.scss";

.bg-loader {
  /* background-color: $bg-color-main;
    height: 100%;
    position: absolute;
    top: 0;
    left: 0;
    width: 100%; */
    position: fixed;
    top: 0;
    left: 0;
    display: flex;
    width: 100%;
    height: 100%;
    background: $bg-color-main;

    img{
        width: 10%;
        position: relative;
        animation: walk 1s infinite linear;
    }
}


@keyframes walk {
  0% {
      transform: rotate(0deg);
  }

  100%{
      transform: rotate(360deg);
  }
}
</style>
