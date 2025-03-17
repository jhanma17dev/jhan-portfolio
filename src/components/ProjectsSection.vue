<template>
  <div class="carousel rounded-box w-full project-carousel relative">
    <div
      v-for="(project, index) in projects"
      :key="index"
      class="carousel-item w-1/3 project-card flex flex-col py-6 px-12 transition duration-900 ease-in-out"
      :class="{
        'active-project-card': project.showDescription && !isHidden(index),
        'hidden-project-card': isHidden(index),
      }"
      @mouseenter="project.showDescription = true"
      @mouseleave="project.showDescription = false"
    >
      <div class="flex flex-row justify-between items-center">
        <div>
          <span class="text-[1.4rem] text-white font-bold">{{
            project.id
          }}</span>
          <br />
          <span class="text-[1.2rem] category-text font-bold">{{
            project.category
          }}</span>
        </div>
        <div class="outline-solid p-2 rounded-lg project-card-icon">
          <svg
            xmlns="http://www.w3.org/2000/svg"
            height="32px"
            viewBox="0 -960 960 960"
            width="32px"
            fill="#e3e3e3"
          >
            <path
              d="M240-120q-45 0-89-22t-71-58q26 0 53-20.5t27-59.5q0-50 35-85t85-35q50 0 85 35t35 85q0 66-47 113t-113 47Zm0-80q33 0 56.5-23.5T320-280q0-17-11.5-28.5T280-320q-17 0-28.5 11.5T240-280q0 23-5.5 42T220-202q5 2 10 2h10Zm230-160L360-470l358-358q11-11 27.5-11.5T774-828l54 54q12 12 12 28t-12 28L470-360Zm-190 80Z"
            />
          </svg>
        </div>
      </div>

      <div class="image-container mt-8">
        <img :src="project.image" alt="" class="project-img" />
      </div>

      <div class="project-info mt-8">
        <h2 class="text-[1.8rem] text-white font-bold">
          {{ project.title }}
        </h2>

        <div class="description-container overflow-hidden">
          <p
            class="text-[1rem] text-gray-200 mt-4 description-text transition-all duration-500 ease-in-out"
            :class="
              project.showDescription
                ? 'description-visible'
                : 'description-hidden'
            "
          >
            {{ project.description }}
          </p>
        </div>

        <div class="mt-4">
          <div
            class="badge badge-soft badge-primary project-badge rounded-sm mr-2"
            v-for="(technology, index) in project.technologies"
            :key="index"
          >
            {{ technology }}
          </div>
        </div>
      </div>
    </div>

    <button class="prev-button" v-if="shownIndex != 0" @click="prevProject()">
      <svg
        xmlns="http://www.w3.org/2000/svg"
        height="24px"
        viewBox="0 -960 960 960"
        width="24px"
        fill="#f04b38"
      >
        <path d="M640-80 240-480l400-400 71 71-329 329 329 329-71 71Z" />
      </svg>
    </button>

    <button
      class="next-button"
      v-if="shownIndex != projects.length - 3"
      @click="nextProject()"
    >
      <svg
        xmlns="http://www.w3.org/2000/svg"
        height="24px"
        viewBox="0 -960 960 960"
        width="24px"
        fill="#f04b38"
      >
        <path d="m321-80-71-71 329-329-329-329 71-71 400 400L321-80Z" />
      </svg>
    </button>
  </div>
</template>

<script setup>
import { reactive, computed, ref } from "vue";

const shownIndex = ref(0);

const showQuantity = ref(3);

const projects = reactive([
  {
    id: "01",
    title: "Project Title",
    category: "Category",
    description:
      "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed vel turpis vel neque vulputate tincidunt. Sed vel turpis vel neque vulputate tincidunt.",
    image:
      "https://cdn.prod.website-files.com/65bb7884c67879aa0d84f24e/65c0eb721ea864f342f436f8_What-are-landing-pages-and-why-do-you-need-to-use-them.jpeg",
    technologies: ["Vue", "Express", "Mongodb"],
    showDescription: false,
  },
  {
    id: "01",
    title: "Project Title",
    category: "Category",
    description:
      "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed vel turpis vel neque vulputate tincidunt. Sed vel turpis vel neque vulputate tincidunt.",
    image:
      "https://assets.justinmind.com/wp-content/uploads/2020/09/landing-page-ux-unbounce.png",
    technologies: ["Vue", "Express", "Mongodb"],
    showDescription: false,
  },
  {
    id: "01",
    title: "Project Title",
    category: "Category",
    description:
      "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed vel turpis vel neque vulputate tincidunt. Sed vel turpis vel neque vulputate tincidunt.",
    image:
      "https://cdn.prod.website-files.com/65bb7884c67879aa0d84f24e/65c0eb721ea864f342f436f8_What-are-landing-pages-and-why-do-you-need-to-use-them.jpeg",
    technologies: ["Vue", "Express", "Mongodb"],
    showDescription: false,
  },
  {
    id: "01",
    title: "Project Title",
    category: "Category",
    description:
      "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed vel turpis vel neque vulputate tincidunt. Sed vel turpis vel neque vulputate tincidunt.",
    image:
      "https://cdn.prod.website-files.com/65bb7884c67879aa0d84f24e/65c0eb721ea864f342f436f8_What-are-landing-pages-and-why-do-you-need-to-use-them.jpeg",
    technologies: ["Vue", "Express", "Mongodb"],
    showDescription: false,
  },
]);

function isHidden(index) {
  return index < shownIndex.value || index >= shownIndex.value + showQuantity.value;
}

function nextProject() {
  shownIndex.value = shownIndex.value + 1;
}

function prevProject() {
  shownIndex.value = shownIndex.value - 1;
}
</script>

<style scoped>
.project-carousel {
  box-sizing: content-box;
  overflow: visible;
  margin: 48px 0;
}

.project-card {
  height: calc(68vw / 3 * 1.4 + 80px);
  box-sizing: border-box;
  border: #fe5944 16px solid;
  background-color: #f04b38;
  border-radius: 24px;
  overflow: hidden;
  transform: translateX(calc(-100% * v-bind(shownIndex)));
}

.project-card-icon {
  outline-color: rgba(240, 255, 255, 0.1);
  height: fit-content;
}

.category-text {
  color: #ffd438;
}

.project-img {
  aspect-ratio: 1 / 1;
  object-fit: cover;
}

.image-container {
  border: solid 12px rgba(255, 255, 255, 1);
  border-radius: 12px;
}

.project-badge {
  background-color: #ffd438;
  color: #f04b38;
  font-weight: bold;
  border: none;
}

.active-project-card {
  height: auto;
  z-index: 2;
  transform: translateX(calc(-100% * v-bind(shownIndex))) scale(1.2);
}

.description-container {
  min-height: 0;
  transition: all 0.5s ease-in-out;
}

.description-text {
  transform-origin: top;
}

.description-visible {
  opacity: 1;
  transform: translateY(0);
  max-height: 200px;
}

.description-hidden {
  opacity: 0;
  transform: translateY(-20px);
  max-height: 0;
}

.prev-button {
  left: -64px;
}

.next-button {
  right: -64px;
}

.next-button,
.prev-button {
  position: absolute;
  top: calc((70vw / 3 * 1.4 + 80px) / 2);
  transform: translateY(-50%);
  z-index: 1;
  background-color: rgb(255, 255, 255);
  border: 16px solid rgba(255, 255, 255, 1);
  border-radius: 50%;
  box-sizing: border-box;
}

.next-button,
.prev-button :hover {
  cursor: pointer;
}

.hidden-project-card {
  opacity: 0;
  z-index: 0;
}
</style>