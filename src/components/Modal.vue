<template>
    <transition name="fade">
      <div v-if="showModal" class="fixed z-10 inset-0 overflow-y-auto">
        <div
          class="flex items-end justify-center min-h-screen pt-4 px-4 pb-20 text-center sm:block sm:p-0"
        >
          <div class="fixed inset-0 transition-opacity" @click="modalToggle(false)">
            <div class="absolute inset-0 bg-gray-500 opacity-75"></div>
          </div>
          <span
            class="hidden sm:inline-block sm:align-middle sm:h-screen"
          ></span>&#8203;
          <div
            class="inline-block align-bottom bg-white rounded-lg text-left overflow-hidden shadow-xl transform transition-all sm:my-8 sm:align-middle sm:max-w-lg md:max-w-2xl lg:max-w-5xl sm:w-full"
            role="dialog"
            aria-modal="true"
            aria-labelledby="modal-headline"
          >
            <div class="bg-white px-4 pt-5 pb-4 sm:p-6 sm:pb-4">
              <div class="sm:flex sm:items-start">
                <div class="mt-3 text-center sm:mt-0 sm:ml-4 sm:text-left w-full">
                  <h3
                    class="text-2xl font-bold leading-6 font-medium text-gray-900"
                    id="modal-headline"
                  >
                    {{ title }}
                  </h3>
                  <div class="mt-8">
                    <slot></slot>
                  </div>
                </div>
              </div>
            </div>
            <div
              class="bg-gray-50 px-4 py-3 sm:px-6 sm:flex sm:flex-row-reverse"
            >
              <span
                class="mt-3 flex w-full rounded-md shadow-sm sm:mt-0 sm:w-auto"
              >
                <button
                  type="button"
                  class="inline-flex justify-center w-full rounded-md border border-gray-300 px-4 py-2 bg-white text-base leading-6 font-medium text-gray-700 shadow-sm hover:text-gray-500 focus:outline-none focus:border-blue-300 focus:shadow-outline-blue transition ease-in-out duration-150 sm:text-sm sm:leading-5"
                  @click="modalToggle(false)"
                >
                  Close
                </button>
              </span>
            </div>
          </div>
        </div>
      </div>
    </transition>
</template>


<script>

export default {
    name: 'Modal',
    props: ['title', 'showModal'],
    data() {
        return {
        }
    },
    methods: {
        modalToggle(val) {
            this.$emit('modal-toggle', val)
        }
    }
}

</script>

<style>
.fade-enter-from,
.fade-leave-to {
  opacity: 0;
  transition: ease 0.2s;
}

.fade-leave-from,
.fade-enter-to {
  opacity: 1;
  transition: ease 0.2s;
}
</style>
