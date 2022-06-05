<script setup>
import { ref } from "vue";

const error = ref(false);
</script>
<template>
  <div class="flex">
    <div class="mb-6 p-4">
      <div
        class="bg-base-100 rounded-lg p-4 shadow-lg w-auto flex flex-col gap-3"
        :class="{ 'shake-enter-active': error }"
      >
        <input type="text" class="input input-bordered" value="Username" />
        <input type="password" class="input input-bordered" value="Password" />
        <button class="btn btn-primary" @click="error = !error">Log In</button>
        <Transition name="shake">
          <div class="alert alert-error shadow-lg overflow-hidden" v-if="error">
            <div>
              <svg
                xmlns="http://www.w3.org/2000/svg"
                class="stroke-current flex-shrink-0 h-6 w-6"
                fill="none"
                viewBox="0 0 24 24"
              >
                <path
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  stroke-width="2"
                  d="M10 14l2-2m0 0l2-2m-2 2l-2-2m2 2l2 2m7-2a9 9 0 11-18 0 9 9 0 0118 0z"
                />
              </svg>
              <span>Error! Login failed.</span>
            </div>
          </div>
        </Transition>
      </div>
    </div>
  </div>
</template>

<style scoped>
.alert-enter-from,
.alert-leave-to {
  opacity: 0;
}
.alert-enter-from {
  height: 0;
}
.alert-enter-active,
.alert-leave-active {
  transition: 0.4s ease;
}

.shake-enter-active,
.shake-leave-active {
  animation: shake 0.3s ease-in-out;
}

@keyframes shake {
  0%,
  100% {
    transform: translateX(0);
  }
  25% {
    transform: translateX(10px);
  }
  75% {
    transform: translateX(-10px);
  }
}
</style>
