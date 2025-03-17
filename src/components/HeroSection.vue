<template>
  <section class="lg:flex items-center">
    <div class="flex flex-3 items-end pr-6 flex-col">
      <span class="role-text mb-12">Desarrollador Web</span>
      <span class="name-text text-end">Jhan Mario Bolivar Peña</span>
      <div class="relative mt-10">
        <a href="#" class="learn-btn">
          Conóceme
          <div class="play-icon flex">
            <svg xmlns="http://www.w3.org/2000/svg" height="24px" viewBox="0 -960 960 960" width="24px" fill="#e3e3e3"><path d="M320-200v-560l440 280-440 280Z"/></svg>
          </div>
        </a>
      </div>
    </div>
    <img
      src="../assets/portfolio-test.png"
      alt=""
      class="object-contain flex-5"
    />
  </section>
</template>

<script setup>
</script>

<style scoped>
.role-text {
  font-size: 1.2rem;
  font-weight: 600;
  color: #ffd438;
  text-transform: uppercase;
  letter-spacing: 0.2rem;
}

.name-text {
  font-size: 6rem;
  font-weight: 600;
  color: white;
  text-transform: uppercase;
  line-height: 1;
  font-family: "Bebas Neue", sans-serif;
}

.learn-btn {
  background: linear-gradient(
    to right,
    #ffd438,
    #ffd438 40px,
    #fe5944 40px,
    #fe5944 44px,
    white 44px,
    white
  );
  color: white;
  padding: 1rem;
  padding-left: 70px;
  font-size: 1rem;
  font-weight: 800;
  text-transform: uppercase;
  letter-spacing: 0.1rem;
  color: #fe5944;
  border-radius: 8px;
}

.play-icon {
  position: absolute;
  height: 24px;
  width: 24px;
  background-color: #fe5944;
  left: 30px;
  top: calc(50% - 12px);
  border-radius: 100%;
}
</style>