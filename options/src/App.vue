<script>
import Menu from "./components/vMenu.vue";

export default {
  name: "App",
  components: { Menu },
  data() {
    return {
      show: false,
    };
  },
};
</script>

<template>
    <button @click="show = !show">Menu</button>
    <transition name="fade">
      <Menu v-show="show" />
    </transition>
</template>

<style >
.fade-enter-from,
.fade-leave-to{
  opacity:0;
}
.fade-enter-active,
.fade-leave-active{
  transition: opacity 0.3s ease;
}
</style>
