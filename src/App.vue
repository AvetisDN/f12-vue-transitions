<script setup>
import { ref } from "vue";
import Keyframes from "./components/Keyframes.vue";
import ElementsTransition from "./components/ElementsTransition.vue";
import Group from "./components/Group.vue";

const card = ref(false);
const card2 = ref(false);
</script>

<template>
  <div class="p-4 min-h-screen w-full bg-base-300">
    <Group />
    <ElementsTransition />
    <Keyframes />
    <div class="flex">
      <div class="p-4 w-[400px]">
        <button class="btn btn-secondary" @click="card = !card">
          Toggle Card
        </button>
        <div class="my-4"></div>
        <Transition
          name="fade"
          @before-enter="() => null"
          @enter="() => null"
          @after-enter="() => null"
          @before-leave="() => null"
          @leave="() => null"
          @after-leave="() => null"
        >
          <div class="card w-96 bg-base-100 shadow-xl" v-if="card">
            <figure>
              <img
                src="https://api.lorem.space/image/shoes?w=400&h=225"
                alt="Shoes"
              />
            </figure>
            <div class="card-body">
              <h2 class="card-title">Shoes!</h2>
              <p>If a dog chews shoes whose shoes does he choose?</p>
              <div class="card-actions justify-end">
                <button class="btn btn-primary">Buy Now</button>
              </div>
            </div>
          </div>
        </Transition>
      </div>
      <div class="p-4 w-[400px]">
        <button class="btn btn-success" @click="card2 = !card2">
          Toggle Card2
        </button>
        <div class="my-4"></div>
        <Transition name="slide-fade">
          <div class="card w-96 bg-base-100 shadow-xl" v-if="card2">
            <figure>
              <img
                src="https://api.lorem.space/image/shoes?w=400&h=225"
                alt="Shoes"
              />
            </figure>
            <div class="card-body">
              <h2 class="card-title">Shoes!</h2>
              <p>If a dog chews shoes whose shoes does he choose?</p>
              <div class="card-actions justify-end">
                <button class="btn btn-primary">Buy Now</button>
              </div>
            </div>
          </div>
        </Transition>
      </div>
    </div>
  </div>
</template>

<style scoped>
.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}

.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s ease;
}

/* .fade-enter-to,
.fade-leave-from {
  opacity: 1;
} */

.slide-fade-enter-from {
  opacity: 0;
  transform: translateY(-30px);
}
.slide-fade-leave-to {
  opacity: 0;
  transform: translateY(30px);
}
.slide-fade-enter-active {
  transition: 0.3s ease;
}
.slide-fade-leave-active {
  transition: 0.8s ease;
}
</style>
