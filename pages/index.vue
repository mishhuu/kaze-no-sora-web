<template>
  <div class="flex flex-col justify-between min-h-screen ...">
    <client-only
      class="text-white grid grid-cols-1 justify-items-center pt-[25%] text-xl font-['RockoUltraFLF']"
      placeholder=" Loading..."
    >
      <div
        class="container right-0 mx-auto flex px-5 md:py-32 py-12 md:flex-row flex-col items-center"
      >
        <div
          class="lg:flex-grow md:w-1/2 lg:pr-24 md:pr-16 flex flex-col md:items-start text-white md:text-left mb-16 md:mb-0 items-center text-center drop-shadow-xl font-['RockoUltraFLF']"
        >
          <strong>
            <div
              class="leading-relaxed text-5xl text-slate-100 md:text-5xl lg:text-6xl xl:text-7xl 2xl:text-8xl hover:text-emerald-100"
            >
              <h1>
                Kaze no
                <span class="text-emerald-300"> Sora </span>
                ♡
              </h1>
            </div>
            <div>
              <h2
                class="text-4xl lg:text-5xl xl:text-6xl 2xl:text-6xl text-slate-100 hover:text-emerald-100 leading-relaxed"
              >
                We are
                <Transition name="fade" mode="out-in">
                  <span
                    class="text-white hover:text-emerald-100"
                    v-if="
                      lista[counter % lista.length] ==
                      `an all-inclusive community to meet all kind of people <3`
                    "
                    id="words"
                    >an
                    <span class="text-emerald-300">all-inclusive</span>
                    community to meet
                    <span class="text-emerald-300">all kind</span> of people
                  </span>
                  <span
                    class="text-emerald-300"
                    v-else-if="lista[counter % lista.length] == `a cute server`"
                    id="words"
                    >{{ lista[counter % lista.length] }}</span
                  >
                  <span
                    class="text-emerald-300"
                    v-else-if="
                      lista[counter % lista.length] == `a diversity server`
                    "
                    id="words"
                    >{{ lista[counter % lista.length] }}</span
                  >
                  <span
                    class="text-emerald-300"
                    v-else-if="lista[counter % lista.length] == `Kaze No Sora!`"
                    id="words"
                    >{{ lista[counter % lista.length] }}</span
                  >
                  <span
                    class="text-emerald-300"
                    v-else-if="
                      lista[counter % lista.length] == `a funny server`
                    "
                    id="words"
                    >{{ lista[counter % lista.length] }}</span
                  >
                </Transition>
              </h2>
            </div>
          </strong>
          <div class="flex justify-center pt-10">
            <NuxtLink to="https://discord.gg/gk7rjCYbHN" target="_blank">
              <button
                class="bg-emerald-600 hover:bg-white hover:text-emerald-500 text-white px-6 pb-2 pt-2.5 text-xs font-medium leading-normal focus:outline-none rounded"
              >
                Join Server
              </button>
            </NuxtLink>
            <button
              class="inline-block ml-2 rounded text-neutral-800 dark:text-zinc-100 bg-neutral-100 dark:bg-zinc-800 px-6 pb-2 pt-2.5 text-xs font-medium uppercase leading-normal black:text-neutral-50 drop-shadow-xl transition duration-150 ease-in-out"
              @click="toggleDark()"
            >
              {{ isDark ? "Light" : "Dark" }}
            </button>
          </div>
        </div>
        <div>
          <h1
            class="leading-relaxed text-3xl text-white md:text-3xl lg:text-4xl text-center pb-2 hover:text-emerald-100 font-['RockoUltraFLF']"
          >
            Server <span class="text-emerald-300">Owner</span>
          </h1>
          <user-card />
        </div>
      </div>
      <footer class="body-font">
        <div class="container px-5 py-8 mx-auto flex items-center flex-col">
          <p
            class="text-sm opacity-70 sm:py-2 drop-shadow-xl sm:mt-0 mt-4 text-white font-['RockoUltraFLF']"
          >
            © 2023 Kaze no Sora
          </p>
        </div>
      </footer>
    </client-only>
  </div>
  <!--
  ⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢀⣀⣀⣀⣀⣀⣀⣀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀
  ⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢀⣀⣤⡶⠾⠛⠛⠋⠉⠉⠉⠉⠉⠛⠛⠻⠶⣦⣤⡀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀
  ⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢀⣤⡶⠟⠋⠁⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠉⠛⠷⣦⣄⣤⣤⣤⣤⣤⣤⣀⠀⠀⠀
  ⠀⠀⠀⠀⠀⠀⠀⠀⠀⢀⣴⠟⠉⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⣀⣀⠀⠈⠙⢿⣄⠀⠀⠀⠉⠙⠻⣦⡀
  ⠀⠀⠀⠀⠀⠀⠀⢀⣴⠟⠁⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⣸⠉⠳⣄⠀⠀⠀⠀⢸⠁⠈⢣⠀⠀⠀⠙⢧⡀⠀⠀⠀⠀⠹⣧
  ⠀⠀⠀⠀⠀⠀⢠⡿⠃⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⣷⠀⠀⠸⡆⠀⠀⠀⠸⣇⠀⠈⣧⠀⠀⠀⠀⠻⣄⠀⠀⠀⠀⣿
  ⠀⠀⠀⠀⠀⣰⡟⠁⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢻⣧⣀⣠⣿⠀⠀⠀⠀⢻⣷⣾⣿⡆⠀⠀⠀⠀⠹⣆⠀⠀⢰⡿
  ⠀⠀⠀⠀⢠⡿⢀⣠⡤⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠈⣿⣿⣿⣿⡇⠀⠀⠀⠘⡿⠿⠟⣇⠀⠀⠀⠀⠀⢹⡆⢀⣿⠃
  ⠀⠀⠀⢠⣾⠿⠋⠁⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢸⡌⠉⠀⡇⠀⠀⠀⠀⠹⡀⠀⡏⢀⣴⣿⣿⣿⠀⢿⡿⠁⠀
  ⠀⢀⣴⠟⠁⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⣴⣶⣶⣶⣶⡄⠀⠳⣤⡼⠁⠀⠀⠀⠀⠀⠙⠚⠁⠈⢛⠟⠛⠉⠀⢸⣧⠀⠀
  ⢀⣾⠋⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠙⠿⠿⠿⠿⠃⠀⠀⠀⠀⠀⣾⡄⠀⣷⡇⠀⠀⠀⠀⠈⠀⠀⠀⠀⠀⣿⠀⠀
  ⣼⠇⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠈⠻⠭⠏⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⣿⠀⠀
  ⣿⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢀⣠⡴⢶⣿⣿⡛⠛⠛⠛⠶⣤⡀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢰⣿⠀⠀
  ⢿⡆⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢀⡴⠞⠋⠁⠐⠛⠛⠋⠀⠀⠀⠀⠀⠈⢷⡀⠀⠀⠀⠀⠀⠀⠀⠀⠀⣸⡇⠀⠀
  ⠈⢿⣦⡀⠀⠀⠀⠀⠀⠀⠀⠀⢀⣀⠀⢀⡴⠋⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢸⡇⠀⠀⠀⠀⠀⠀⠀⠀⢠⣿⠁⠀⠀
  ⠀⠀⠉⠛⠷⢶⣶⠶⠶⠶⠖⠛⠋⠁⣴⠏⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢸⡇⠀⠀⠀⠀⠀⠀⠀⢀⣾⠃⠀⠀⠀
  ⠀⠀⠀⠀⠀⠀⢻⣦⠀⠀⠀⠀⠀⣼⠃⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⣼⠁⠀⠀⠀⠀⠀⠀⢠⣾⠃⠀⠀⠀⠀
  ⠀⠀⠀⠀⠀⠀⠀⠹⣷⣀⠀⠀⢰⡇⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢰⡏⠀⠀⠀⠀⠀⢀⣴⡿⠁⠀⠀⠀⠀
  ⠀⠀⠀⠀⠀⠀⠀⠀⠈⠻⣶⣄⣸⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢠⡟⠀⠀⠀⠀⢀⣤⣿⠏⠀⠀⠀⠀⠀
  ⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠈⠛⣿⡀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢠⡟⠀⠀⠀⣠⡴⠋⣹⡏⠀⠀⠀⠀⠀⠀⠀
  ⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢸⣧⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢀⣴⣋⣠⡴⠶⠛⠁⠀⣰⡟⠀⠀⠀⠀⠀⠀⠀⠀⠀
  ⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠻⣷⣄⠀⠀⠀⠀⠀⠀⠀⠀⠀⢀⡴⠟⠉⠉⠀⠀⠀⠀⠀⣴⡟⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀
  ⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠈⠻⢷⣤⣄⣀⣀⣀⣤⡴⠞⠋⠀⠀⠀⠀⠀⠀⠀⢀⣼⠏⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀
  ⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠈⢻⡇⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⣰⡿⠃⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀
  ⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠘⣿⡀⠀⠀⠀⠀⢀⣤⣶⠆⢀⣠⡾⠋⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀
  ⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠹⣷⣄⠀⠀⠀⠙⣛⣡⣶⠟⠋⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀
  -->
</template>

<style>
/* we will explain what these classes do next! */
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s ease;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}
</style>
<script setup lang="js">
import { useInterval, useDark, useToggle } from '@vueuse/core'
var lista = ["an all-inclusive community to meet all kind of people <3", "a funny server", "a cute server", "a diversity server", "Kaze No Sora!"];
const counter = useInterval(5000, () => {
  // Incrementa el valor para cambiar el texto
});
const colorMode = useColorMode()
const isDark = useDark()
const toggleDark = useToggle(isDark)
</script>
