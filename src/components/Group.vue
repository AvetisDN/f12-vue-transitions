<script setup>
import { ref } from "vue";
const newFruit = ref("");
const list = ref(["🍎 Apple", "🍊 Orange", "🥝 Kiwi"]);
const addNew = () => {
  const randomIndex = Math.floor(Math.random() * list.value.length);
  list.value.splice(randomIndex, 0, newFruit.value);
  newFruit.value = "";
};
</script>
<template>
  <div class="p-4 mb-6">
    <form @submit.prevent="addNew">
      <input
        type="text"
        class="input input-bordered mb-4"
        placeholder="Add fruit..."
        v-model="newFruit"
      />
    </form>
    <TransitionGroup appear name="list" tag="ul">
      <li v-for="fruit in list" :key="fruit" class="text-xl mb-2 font-bold">
        {{ fruit }}
      </li>
    </TransitionGroup>
  </div>
</template>

<style>
.list-enter-active,
.list-leave-active {
  transition: all 0.3s ease;
}
.list-enter-from,
.list-leave-to {
  opacity: 0;
  transform: translateX(30px);
}
</style>
