<script setup>
import Navbar from "./components/NavBar.vue"
import axios from "axios"
import { ref } from "vue"
import { useToast } from "vue-toastification"

// Get toast interface
const toast = useToast()

const message = ref("")
const firstname = ref("")
const surname = ref("")
const phone = ref("")
const email = ref("")

const send = async () => {
  try {
    let data = {
      message: message.value,
      firstname: firstname.value,
      surname: surname.value,
      email: email.value,
      phone: phone.value,
    }
    const resp = await axios.post(`https://www.polevkoveokynko.cz/api/rautnamiru/`, data)

    toast.success("Poptávka byla odeslána", {
      timeout: 2000,
    })
  } catch (err) {
    console.log(err)
    toast.error("Něco se pokazilo. Zkuste to prosím později, případně nás kontakujte.", {
      timeout: 2000,
    })
  }
}
</script>

<template>
  <div class="min-h-screen layout">
    <Navbar id="item-0" />
    <div id="intro">
      <img
        src="./assets/three.jpg"
        alt="Walnut card tray  with white powder coated steel divider and 3 punchout holes."
        class="w-screen bg-gray-100 rounded-lg md:hidden"
      />
      <div class="bg-white">
        <div class="grid items-center max-w-2xl grid-cols-1 px-4 py-24 mx-auto gap-y-16 gap-x-8 sm:px-6 sm:py-32 lg:max-w-7xl lg:px-8 lg:grid-cols-2">
          <div>
            <h2 class="text-3xl font-extrabold tracking-tight text-gray-900 sm:text-4xl">RAUT NA MÍRU</h2>
            <p class="mt-4 text-gray-500">Ke každému přistupujeme individuálně.</p>

            <dl class="grid grid-cols-1 mt-16 gap-x-6 gap-y-10 sm:grid-cols-2 sm:gap-y-16 lg:gap-x-8">
              <div class="pt-4 border-t border-gray-200">
                <dt class="font-medium text-gray-900">Soukromé</dt>
                <dd class="mt-2 text-sm text-gray-500">
                  Máte narozeniny a nechce se Vám připravovat pohoštění? Řešíte catering na svatbu a pořád se s nikým nemůžete domluvit? Vždy se snažíme vyhovět
                  individuálním potřebám, proto neváhejte a napište nám. :)
                </dd>
              </div>

              <div class="pt-4 border-t border-gray-200">
                <dt class="font-medium text-gray-900">Firemní</dt>
                <dd class="mt-2 text-sm text-gray-500">
                  Zajišťujeme občerstvení na jednorázové firemní akce, meetingy, teambuildingy aj. Je možné se také domluvit na pravidelných rozvozech svačin
                  nebo obědů.
                </dd>
              </div>

              <div class="pt-4 border-t border-gray-200">
                <dt class="font-medium text-gray-900">Pronájem vybavení</dt>
                <dd class="mt-2 text-sm text-gray-500">
                  Nemáte dostatek vybavení na akci? Zapůjčíme Vám gastro zařízení jako je ledovač, kávovar, pípa, dále pak nádoby, talíře, příbory.
                </dd>
              </div>

              <div class="pt-4 border-t border-gray-200">
                <dt class="font-medium text-gray-900">Pronájem prostor</dt>
                <dd class="mt-2 text-sm text-gray-500">
                  V našich prostorech je možnost zorganizovat akci nejrůznějšího typu (narozeniny, koncerty, vernisáže, přednášky apod.)
                </dd>
              </div>
            </dl>
          </div>
          <div class="grid grid-cols-1 grid-rows-2 gap-4 md:grid-cols-2 sm:gap-6 lg:gap-8">
            <img
              src="./assets/two.jpg"
              alt="Walnut card tray with white powder coated steel divider and 3 punchout holes."
              class="bg-gray-100 rounded-lg my-img"
            />
            <img
              src="./assets/three.jpg"
              alt="Top down view of walnut card tray with embedded magnets and card groove."
              class="hidden bg-gray-100 rounded-lg md:block my-img h-100"
            />
            <img src="./assets/one.jpg" alt="Side of walnut card tray with card groove and recessed card area." class="bg-gray-100 rounded-lg my-img" />
            <img
              src="./assets/four.jpg"
              alt="Walnut card tray filledwith cards and card angled in dedicated groove."
              class="hidden bg-gray-100 rounded-lg my-img md:block h-100"
            />
          </div>
        </div>
      </div>
      <div id="contact" class="w-full py-8 bg-gradient-to-r from-pink-500 to-violet-500">
        <form class="w-full max-w-lg px-3 mx-auto">
          <h2 class="pt-10 mb-4 text-2xl font-extrabold tracking-tight text-left text-gray-900 sm:text-2xl">Online rezervace</h2>
          <!--  <div class="flex flex-wrap mb-4 -mx-3">
            <div class="w-full px-3 mb-4 md:w-1/2 md:mb-0">
              <label class="block mb-2 text-xs font-bold tracking-wide text-gray-700 uppercase" for="grid-first-name"> Jméno</label>
              <input
                class="block w-full px-4 py-3 mb-3 leading-tight text-gray-700 bg-gray-200 rounded appearance-none focus:outline-none focus:bg-white"
                id="grid-first-name"
                type="text"
                v-model="firstname"
              />
            </div>
            <div class="w-full px-3 md:w-1/2">
              <label class="block mb-2 text-xs font-bold tracking-wide text-gray-700 uppercase" for="grid-last-name"> Příjmení </label>
              <input
                class="block w-full px-4 py-3 leading-tight text-gray-700 bg-gray-200 border-gray-200 rounded appearance-none focus:outline-none focus:bg-white focus:border-gray-500"
                id="grid-last-name"
                type="text"
                v-model="surname"
              />
            </div>
          </div> -->
          <!--   <div class="flex flex-wrap mb-4 -mx-3">
            <div class="w-full px-3 mb-4 md:w-1/2 md:mb-0">
              <label class="block mb-2 text-xs font-bold tracking-wide text-gray-700 uppercase" for="grid-first-name"> Email</label>
              <input
                class="block w-full px-4 py-3 mb-3 leading-tight text-gray-700 bg-gray-200 rounded appearance-none focus:outline-none focus:bg-white"
                id="grid-first-name"
                type="text"
                v-model="email"
              />
            </div>
            <div class="w-full px-3 md:w-1/2">
              <label class="block mb-2 text-xs font-bold tracking-wide text-gray-700 uppercase" for="grid-last-name"> Telefon </label>
              <input
                v-model="phone"
                class="block w-full px-4 py-3 leading-tight text-gray-700 bg-gray-200 border-gray-200 rounded appearance-none focus:outline-none focus:bg-white focus:border-gray-500"
                id="grid-last-name"
                type="text"
              />
            </div>
          </div> -->
          <!--   <div class="flex flex-wrap mb-4">
            <div class="w-full">
              <label class="block mb-2 text-xs font-bold tracking-wide text-gray-700 uppercase" for="grid-password"> Zpráva </label>
              <textarea
                v-model="message"
                class="block w-full h-48 px-4 py-3 mb-3 leading-tight text-gray-700 bg-gray-200 border-gray-200 rounded appearance-none resize-none no-resize focus:outline-none focus:bg-white focus:border-gray-500"
                id="message"
              ></textarea>
              <p class="text-sm text-white">Odesláním formuláře souhlasíte se zpracováním vašich dat za účelem vyřízení poptávky.</p>
            </div>
          </div> -->
          <div class="justify-start mb-4 md:flex md:items-center">
            <div class="flex justify-start md:w-full">
              <button
                @click="send()"
                class="w-full px-4 py-2 font-bold text-white bg-black rounded shadow md:w-auto hover:bg-teal-500 focus:shadow-outline focus:outline-none"
                type="button"
              >
                Rezervovat
              </button>
            </div>
          </div>
        </form>
      </div>
    </div>

    <div class="flex items-center w-screen h-full mx-auto text-sm text-white bg-black ju md:justify-between">
      <div class="flex flex-col items-center md:items-start md:mx-auto md:flex-row">
        <div class="w-full my-4 text-center md:text-left md:w-auto md:mr-32">
          <p>Telefon: +420 608 824 463</p>
          <p>E-mail: <a href="mailto:rautnamiru@email.cz">rautnamiru@email.cz </a></p>
          <p class="mb-4">Adresa: Koliště 1907/3, 602 00 Brno-střed </p>
          <!--  </div> -->

          <!--   <div class="w-full my-4 text-left md:w-auto md:text-right md:ml-32"> -->
          <p>NakupRum s.r.o.</p>
          <p>IC 09305271</p>
          <p>Koliště 1907/3</p>
        </div>
        <div class="flex flex-col items-center justify-center w-screen md:w-auto md:items-start md:justify-start">
          <a href="https://www.oblast.cz">
            <img
              src="./assets/oblast.jpg"
              alt="Side of walnut card tray with card groove and recessed card area."
              class="top-0 w-32 h-16 mr-4 bg-gray-100 rounded-lg cursor-pointer md:mt-4 item__filter"
            />
          </a>
          <a href="https://www.polevkoveokynko.cz">
            <img
              src="./assets/logoAlt.png"
              alt="Side of walnut card tray with card groove and recessed card area."
              class="h-6 mt-6 mb-6 bg-gray-100 md:mb-0 w-36 cursor-point object-fit item__filter"
            />
          </a>
        </div>
      </div>
    </div>
  </div>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  min-height: 100vh;
}

.gradient {
  background: rgb(47, 47, 47);
  background: linear-gradient(90deg, rgb(37, 58, 40), rgba(65, 150, 70, 1) 100%);
}

.item__filter {
  filter: invert(100%) sepia(100%) saturate(0%) hue-rotate(180deg) brightness(105%) contrast(102%);
  opacity: 1;
  transition: 1s;
}

label {
  color: white !important;
}

html {
  scroll-behavior: smooth;
}

.my-img {
  height: 420px;
  width: 360px;
}
</style>
