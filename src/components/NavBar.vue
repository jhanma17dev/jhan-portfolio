<template>
  <div class="navbar bg-white floating-navbar px-6 transition duration-900 ease-in-out" :class="{'hide-navbar': !showNavbar}">
    <div class="navbar-start">
      <a class="uppercase text-xl">Jhan Bolivar</a>
    </div>
    <div class="navbar-center hidden lg:flex">
      <ul class="menu menu-horizontal px-1 space-x-4 text-lg">
        <li><a>Sobre mi</a></li>
        <li><a>Proyectos</a></li>
        <li><a>Estudios</a></li>
      </ul>
    </div>
    <div class="navbar-end space-x-3">
      <button class="btn btn-circle btn-outline">
        LI
      </button>
      <button class="btn btn-circle btn-outline">
        Git
      </button>
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";

const showNavbar = ref(true);

let prev = window.scrollY;

window.addEventListener('scroll', function(){
  let current = window.scrollY;

  if(prev >= current || current < 200){
    showNavbar.value = true;
  }
  else {
    showNavbar.value = false;
  }

  prev = current;
})


</script>

<style scoped>
.floating-navbar {
  position: fixed;
  top: 1rem;
  left: 50%;
  transform: translateX(-50%);
  z-index: 100;
  width: 90%;
  max-width: 1200px;
  border-radius: 1rem;
  box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1),
    0 2px 4px -1px rgba(0, 0, 0, 0.06);
  height: 96px;
  color: #fe5944;
  font-weight: bolder;
}

.hide-navbar {
  opacity: 0;
  transform: translateY(-200px) translateX(-50%);
}
</style>