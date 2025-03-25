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
      @mouseenter="handleShowDescription(index)"
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
            class="text-[1rem] text-gray-200 mt-4 description-text transition-all duration-900 ease-in-out"
            :class="
              project.showDescription
                ? 'description-visible'
                : 'description-hidden'
            "
          >
            {{ project.description }}
          </p>
        </div>

        <div class="mt-4 mb-6">
          <div
            class="badge badge-soft badge-primary project-badge rounded-sm mr-2"
            v-for="(technology, index) in project.technologies"
            :key="index"
          >
            {{ technology }}
          </div>
        </div>
      </div>

      <div
        href="#"
        class="transition-all duration-900 ease-in-out"
        :class="{
          'learn-btn': project.showDescription,
          'minimized-learn-btn': !project.showDescription,
        }"
      >
        <div class="tooltip mr-4">
          <div class="tooltip-content">
            <div class="text-primary font-bold normal-case text-xs">
              Ver en Github
            </div>
          </div>
          <button
            class="btn btn-ghost btn-circle"
          >
            <svg
              :width="project.showDescription ? '32px' : '0'"
              :height="project.showDescription ? '32px' : '0'"
              viewBox="0 0 192 192"
              fill="none"
              class="transition-all duration-900 ease-in-out "
              :class="{
                'hidden-text': !project.showDescription,
              }"
            >
              <g stroke-width="0"></g>
              <g stroke-linecap="round" stroke-linejoin="round"></g>
              <g>
                <path
                  stroke="#f04b38"
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  stroke-width="12"
                  d="M120.755 170c.03-4.669.059-20.874.059-27.29 0-9.272-3.167-15.339-6.719-18.41 22.051-2.464 45.201-10.863 45.201-49.067 0-10.855-3.824-19.735-10.175-26.683 1.017-2.516 4.413-12.63-.987-26.32 0 0-8.296-2.672-27.202 10.204-7.912-2.213-16.371-3.308-24.784-3.352-8.414.044-16.872 1.14-24.785 3.352C52.457 19.558 44.162 22.23 44.162 22.23c-5.4 13.69-2.004 23.804-.987 26.32C36.824 55.498 33 64.378 33 75.233c0 38.204 23.149 46.603 45.2 49.067-3.551 3.071-6.719 9.138-6.719 18.41 0 6.416.03 22.621.059 27.29M27 130c9.939.703 15.67 9.735 15.67 9.735 8.834 15.199 23.178 10.803 28.815 8.265"
                ></path>
              </g>
            </svg>
          </button>
        </div>

        <div class="tooltip">
          <div class="tooltip-content">
            <div class="text-primary font-bold normal-case text-xs">
              Ver Demo
            </div>
          </div>
          <button
            class="btn btn-ghost btn-circle"
          >
            <svg
              :width="project.showDescription ? '32px' : '0'"
              :height="project.showDescription ? '32px' : '0'"
              viewBox="0 0 20 20"
              fill="none"
              class="transition-all duration-900 ease-in-out"
              :class="{
                'hidden-text': !project.showDescription,
              }"
            >
              <g stroke-width="0"></g>
              <g
                stroke-linecap="round"
                stroke-linejoin="round"
              ></g>
              <g>
                <path
                  fill-rule="evenodd"
                  clip-rule="evenodd"
                  d="M1.25 10C1.25 14.8325 5.16751 18.75 10 18.75C14.8325 18.75 18.75 14.8325 18.75 10C18.75 5.16751 14.8325 1.25 10 1.25C5.16751 1.25 1.25 5.16751 1.25 10ZM17.25 10C17.25 14.0041 14.0041 17.25 10 17.25C5.99594 17.25 2.75 14.0041 2.75 10C2.75 5.99594 5.99594 2.75 10 2.75C14.0041 2.75 17.25 5.99594 17.25 10Z"
                  fill="#f04b38"
                ></path>
                <path
                  fill-rule="evenodd"
                  clip-rule="evenodd"
                  d="M6.25 10C6.25 14.5222 7.74111 18.25 10 18.25C12.2589 18.25 13.75 14.5222 13.75 10C13.75 5.47778 12.2589 1.75 10 1.75C7.74111 1.75 6.25 5.47778 6.25 10ZM12.25 10C12.25 13.7621 11.0548 16.75 10 16.75C8.94518 16.75 7.75 13.7621 7.75 10C7.75 6.23795 8.94518 3.25 10 3.25C11.0548 3.25 12.25 6.23795 12.25 10Z"
                  fill="#f04b38"
                ></path>
                <path
                  d="M3.60174 5.46733L4.60789 4.35483C4.70859 4.4459 4.817 4.53499 4.9328 4.62175C6.2041 5.57424 8.2323 6.16108 10.4482 6.16108C12.3391 6.16108 14.1005 5.73495 15.3792 5.00363C15.687 4.82759 15.9613 4.63663 16.1979 4.43451L17.1722 5.57496C16.8622 5.83981 16.511 6.08431 16.1239 6.3057C14.6076 7.17293 12.5898 7.66108 10.4482 7.66108C7.92613 7.66108 5.58282 6.98307 4.03339 5.82219C3.88117 5.70814 3.73712 5.58977 3.60174 5.46733Z"
                  fill="#f04b38"
                ></path>
                <path
                  d="M3.60174 14.5486L4.60789 15.6611C4.70859 15.57 4.817 15.4809 4.9328 15.3941C6.2041 14.4417 8.2323 13.8548 10.4482 13.8548C12.3391 13.8548 14.1005 14.2809 15.3792 15.0123C15.687 15.1883 15.9613 15.3793 16.1979 15.5814L17.1722 14.4409C16.8622 14.1761 16.511 13.9316 16.1239 13.7102C14.6076 12.843 12.5898 12.3548 10.4482 12.3548C7.92613 12.3548 5.58282 13.0328 4.03339 14.1937C3.88117 14.3078 3.73712 14.4261 3.60174 14.5486Z"
                  fill="#f04b38"
                ></path>
                <path
                  d="M1.75 10.75V9.25H18.25V10.75H1.75Z"
                  fill="#f04b38"
                ></path>
              </g>
            </svg>
          </button>
        </div>

        <div
          class="play-icon flex"
          :class="{
            'show-icon': project.showDescription,
          }"
        >
          <svg
            xmlns="http://www.w3.org/2000/svg"
            height="24px"
            viewBox="0 -960 960 960"
            width="24px"
            :fill="project.showDescription ? '#ffffff' : '#f04b38'"
          >
            <path d="M320-200v-560l440 280-440 280Z" />
          </svg>
        </div>
      </div>
    </div>

    <button class="prev-button" v-if="shownIndex != 0" @click="prevProject(), startTransition()">
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
      @click="nextProject(), startTransition()"
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

const isTransition = ref(false);

function startTransition() {
  isTransition.value = true;

  setTimeout(() => {
    isTransition.value = false;
  }, 900);
}

function handleShowDescription(index) {
  if(!isTransition.value){
    projects[index].showDescription = true
  }
}

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
    id: "02",
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
    id: "03",
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
    id: "04",
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
  return (
    index < shownIndex.value || index >= shownIndex.value + showQuantity.value
  );
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
  height: fit-content;
  box-sizing: border-box;
  border: #fe5944 16px solid;
  background-color: #f04b38;
  border-radius: 24px;
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
  aspect-ratio: 4 / 3;
  object-fit: cover;
}

.image-container {
  position: relative;
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

.learn-btn {
  background: linear-gradient(
    to right,
    #ffd438,
    #ffd438 32px,
    white 32px,
    white
  );
  color: white;
  padding: 0 1rem;
  padding-left: 56px;
  text-transform: uppercase;
  color: #fe5944;
  border-radius: 8px;
  position: absolute;
  bottom: calc(-1.5rem);
  height: 48px;
  display: flex;
  align-items: center;
  box-shadow: 0 0 16px rgba(138, 43, 32, 0.4);
}

.minimized-learn-btn {
  background-color: white;
  color: #f04b38;
  border-radius: 50%;
  position: absolute;
  bottom: calc(-1.5rem);
  height: 48px;
  width: 48px;
  display: flex;
  align-items: center;
  justify-content: center;
  box-shadow: 0 0 16px rgba(138, 43, 32, 0.4);
}

.play-icon {
  position: absolute;
  height: 24px;
  width: 24px;
  top: calc(50% - 12px);
  border-radius: 100%;
}

.hidden-text {
  position: absolute;
}

.show-icon {
  background-color: #f04b38;
  left: 20px;
}
</style>