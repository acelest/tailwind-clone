<template>
  <div>
    <div class="fixed top-10 right-5 z-50">
      <span class="relative flex h-3 w-3">
        <!-- <span
          class="animate-ping absolute inline-flex h-full w-full rounded-full bg-sky-400 opacity-75"
        ></span> -->
        <span
          class="inline-flex rounded-full h-5 w-5 absolute bg-green-500 right-2 top-2"
        ></span>
      </span>
    </div>
    <div
      class="h-[1px] w-full bg-gradient-to-r from-transparent via-gray-200/10 to-transparent"
    ></div>
    <header class="relative z-50 w-full">
      <nav
        :class="[
          'fixed top-0 z-50 w-full bg-[#eeeeee] backdrop-blur border-b-1 border-t-0 border border-gray-600 border-opacity-30',
          isScrolled ? 'shadow-md' : '',
        ]"
      >
        <div class="mx-auto max-w-7xl px-6 sm:px-6 lg:px-8">
          <div class="relative flex h-16 items-center justify-between">
            <!-- Logo -->
            <div class="flex items-center">
              <button
                @click="isMenuOpen = !isMenuOpen"
                type="button"
                class="lg:hidden mr-4 text-slate-900"
              >
                <span class="sr-only">Menu principal</span>
                <svg
                  class="h-6 w-6"
                  fill="none"
                  viewBox="0 0 24 24"
                  stroke-width="1.5"
                  stroke="currentColor"
                >
                  <path
                    stroke-linecap="round"
                    stroke-linejoin="round"
                    d="M3.75 6.75h16.5M3.75 12h16.5m-16.5 5.25h16.5"
                  />
                </svg>
              </button>
              <a href="/" class="flex items-center">
                <img class="h-8 w-auto" src="/favicon.ico" alt="Tailwind CSS" />
              </a>
            </div>

            <!-- Navigation principale -->
            <div
              class="hidden lg:flex lg:items-center lg:gap-x-8 lg:ml-auto lg:mr-16"
            >
              <a
                v-for="(link, index) in [
                  'Docs',
                  'Components',
                  'Blog',
                  'Showcase',
                ]"
                :key="index"
                href="#"
                class="text-sm font-semibold text-slate-900 transition-colors duration-200 hover:text-slate-700"
                >{{ link }}</a
              >
            </div>

            <!-- Menu mobile -->
            <transition
              enter-active-class="transition ease-out duration-200"
              enter-from-class="-translate-x-full"
              enter-to-class="translate-x-0"
              leave-active-class="transition ease-in duration-200"
              leave-from-class="translate-x-0"
              leave-to-class="-translate-x-full"
            >
              <div
                v-show="isMenuOpen"
                class="lg:hidden fixed inset-y-0 left-0 w-64 bg-[#eeeeee] border-black shadow-lg transform"
              >
                <!-- Bouton de fermeture -->
                <button
                  @click="isMenuOpen = false"
                  class="absolute top-4 right-4 p-2 text-slate-900 hover:text-slate-700 transition-colors duration-200"
                >
                  <span class="sr-only">Fermer le menu</span>
                  <svg
                    class="h-6 w-6"
                    fill="none"
                    viewBox="0 0 24 24"
                    stroke-width="1.5"
                    stroke="currentColor"
                  >
                    <path
                      stroke-linecap="round"
                      stroke-linejoin="round"
                      d="M6 18L18 6M6 6l12 12"
                    />
                  </svg>
                </button>

                <div class="pt-20 px-4 bg-white">
                  <div class="space-y-6">
                    <a
                      v-for="(link, index) in [
                        'Docs',
                        'Components',
                        'Blog',
                        'Showcase',
                      ]"
                      :key="index"
                      href="#"
                      class="block text-base font-medium text-slate-900 hover:text-slate-700 transition-colors duration-200 py-2 border-b border-gray-200"
                      >{{ link }}</a
                    >
                  </div>

                  <!-- Boutons sociaux en bas -->
                  <div class="mt-8 flex items-center gap-4">
                    <a href="#" class="text-slate-900 hover:text-slate-700">
                      <span class="sr-only">Search</span>
                      <svg
                        class="h-6 w-6"
                        fill="none"
                        viewBox="0 0 24 24"
                        stroke-width="1.5"
                        stroke="currentColor"
                      >
                        <path
                          stroke-linecap="round"
                          stroke-linejoin="round"
                          d="M21 21l-5.197-5.197m0 0A7.5 7.5 0 105.196 5.196a7.5 7.5 0 0010.607 10.607z"
                        />
                      </svg>
                    </a>
                    <!-- <a
                      href="https://github.com/tailwindlabs/tailwindcss"
                      class="text-slate-900 hover:text-slate-700"
                    >
                      <span class="sr-only">GitHub</span>
                      <svg
                        viewBox="0 0 16 16"
                        class="h-6 w-6"
                        fill="currentColor"
                      >
                        <path
                          d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"
                        />
                      </svg>
                    </a> -->
                  </div>
                </div>
              </div>
            </transition>

            <!-- Overlay pour fermer le menu au clic -->
            <transition
              enter-active-class="transition-opacity ease-linear duration-300"
              enter-from-class="opacity-0"
              enter-to-class="opacity-100"
              leave-active-class="transition-opacity ease-linear duration-300"
              leave-from-class="opacity-100"
              leave-to-class="opacity-0"
            >
              <div
                v-show="isMenuOpen"
                class="lg:hidden fixed inset-0 bg-black bg-opacity-25"
                @click="isMenuOpen = false"
              ></div>
            </transition>

            <!-- Boutons droite -->
            <div class="flex items-center gap-x-5">
              <!-- <a
                href="#"
                class="hidden lg:block text-sm font-semibold text-slate-900 transition-colors duration-200 hover:text-slate-700"
              >
                <span class="sr-only">Search</span>
                <svg
                  class="h-6 w-6"
                  fill="none"
                  viewBox="0 0 24 24"
                  stroke-width="1.5"
                  stroke="currentColor"
                >
                  <path
                    stroke-linecap="round"
                    stroke-linejoin="round"
                    d="M21 21l-5.197-5.197m0 0A7.5 7.5 0 105.196 5.196a7.5 7.5 0 0010.607 10.607z"
                  />
                </svg>
              </a> -->
              <!-- <a
                href="https://github.com/tailwindlabs/tailwindcss"
                class="hidden lg:block text-sm font-semibold text-slate-900 transition-colors duration-200 hover:text-slate-700"
              >
                <span class="sr-only">Tailwind CSS on GitHub</span>
                <svg viewBox="0 0 16 16" class="h-6 w-6" fill="currentColor">
                  <path
                    d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"
                  />
                </svg>
              </a> -->
              <a
                href="#"
                class="rounded-lg px-4 py-2 text-sm font-semibold text-black bg-white hover:bg-gray-100 transition-colors duration-200"
              >
                Sign in
              </a>
              <a
                href="#"
                class="rounded-lg bg-slate-900 px-4 py-2 text-sm font-semibold text-white hover:bg-slate-700 transition-colors duration-200 flex items-center gap-2"
              >
                Sign up
                <span class="relative flex h-3 w-3">
                  <span
                    class="animate-ping absolute inline-flex h-full w-full rounded-full bg-sky-400 opacity-75"
                  ></span>
                  <span
                    class="relative inline-flex rounded-full h-3 w-3 bg-green-500"
                  ></span>
                </span>
              </a>
            </div>
          </div>
        </div>
      </nav>
    </header>
  </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from "vue";

const isScrolled = ref(false);
const isMenuOpen = ref(false);

// Fermer le menu avec la touche Escape
const handleEscape = (e) => {
  if (e.key === "Escape" && isMenuOpen.value) {
    isMenuOpen.value = false;
  }
};

onMounted(() => {
  window.addEventListener("scroll", () => {
    isScrolled.value = window.scrollY > 0;
  });
  document.addEventListener("keydown", handleEscape);
});

onUnmounted(() => {
  document.removeEventListener("keydown", handleEscape);
});
</script>
