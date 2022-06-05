<script setup>
import { ref } from "vue";

const state = ref("primary");
</script>
<template>
  <div class="p-4 mb-6 h-20 relative">
    <Transition name="slide-up">
      <div v-if="state === 'primary'">
        <button
          class="btn btn-primary block absolute"
          @click="state = 'secondary'"
        >
          Primary
        </button>
      </div>
      <div v-else-if="state === 'secondary'">
        <button
          class="btn btn-secondary block absolute"
          @click="state = 'success'"
        >
          Secondary
        </button>
      </div>
      <div v-else-if="state === 'success'">
        <button
          class="btn btn-success block absolute"
          @click="state = 'primary'"
        >
          Success
        </button>
      </div>
    </Transition>
  </div>
</template>

<style scoped>
.slide-up-enter-from {
  opacity: 0;
  transform: translateY(30px);
}
.slide-up-leave-to {
  opacity: 0;
  transform: translateY(-30px);
}
.slide-up-enter-active,
.slide-up-leave-active {
  transition: all 0.5s ease;
}
.slide-up-enter-to,
.slide-up-leave-from {
  opacity: 1;
  transform: translateY(0);
}
</style>
