<template>
     <main class="bg-white p-8 w-full m-5 border-2 border-slate-200 border-solid rounded-xl">
          <header>
               <h1 class="text-5xl font-bold text-slate-700">Deals</h1>

               <nav>
                    <ul class="flex mt-5 font-medium">
                         <li v-for="label in labels" :key="label.id" class="cursor-pointer" @click="filterItems(label.name)" :class="currentStatue === label.name ? 'px-5 border-b-2 border-black text-black' : ' hover:text-slate-500 text-slate-300 px-5 border-b-2 border-slate-300'">{{ label.label }} ({{ countItemsStatus(label.name) }})</li>
                    </ul>
                    <ul class="flex justify-between">
                         <li>
                              <ul class="flex items-center gap-x-3">
                                   <li>
                                        <div class="grid grid-cols-[30px_1fr_50px] h-10 items-center bg-white border-slate-200 border-solid border-2 rounded-md">
                                             <div class="flex w-full h-full justify-center items-center">
                                                  <img src="/images/icons/search.png" alt="" class="w-4 h-4" />
                                             </div>
                                             <input type="text" v-model="search" placeholder="Search object" id="search_object" class="w-full h-full outline-none" />
                                             <div class="flex justify-center items-center bg-slate-200 rounded-lg mr-1 p-1">
                                                  <img src="/images/icons/macos_cmd.svg" alt="" class="mr-1" />
                                                  <span class="font-normal">K</span>
                                             </div>
                                        </div>
                                   </li>
                                   <li class="text-slate-400 font-medium my-5">
                                        <button class="px-4 h-10 gap-x-3 border-2 border-slate-200 border-solid w-fit hover:bg-slate-100 text-black bg-white w-full rounded-lg font-medium flex items-center justify-center"><span class="text-slate-500">Object</span> <img src="/images/icons/arrow_down.svg" alt="" class="" /></button>
                                   </li>
                                   <li class="text-slate-400 font-medium my-5">
                                        <button class="px-4 h-10 gap-x-3 border-2 border-slate-200 border-solid w-fit hover:bg-slate-100 text-black bg-white w-full rounded-lg font-medium flex items-center justify-center"><span class="text-slate-500">Company</span> <img src="/images/icons/arrow_down.svg" alt="" class="" /></button>
                                   </li>
                                   <li class="text-slate-400 font-medium my-5">
                                        <button class="px-4 h-10 gap-x-3 border-2 border-slate-200 border-solid w-fit hover:bg-slate-100 text-black bg-white w-full rounded-lg font-medium flex items-center justify-center"><span class="text-slate-500">Statue</span> <img src="/images/icons/arrow_down.svg" alt="" class="" /></button>
                                   </li>
                              </ul>
                         </li>
                         <li>
                              <ul class="flex items-center gap-x-5">
                                   <li>
                                        <button class="px-4 h-10 gap-x-3 border-2 border-slate-200 border-solid w-fit hover:bg-slate-200 bg-white w-full rounded-lg font-medium flex items-center justify-center">
                                             <img src="/images/icons/share.svg" alt="" class="" />
                                             <span class="text-black">Export</span>
                                        </button>
                                   </li>
                                   <li class="text-slate-400 font-medium my-5">
                                        <button class="px-4 h-10 gap-x-3 border-2 border-slate-200 border-solid w-fit hover:bg-slate-700 bg-slate-800 w-full rounded-lg font-medium flex items-center justify-center">
                                             <img src="/images/icons/new_folder.svg" alt="" class="" />
                                             <span class="text-white">New Deal</span>
                                        </button>
                                   </li>
                              </ul>
                         </li>
                    </ul>
               </nav>
          </header>

          <table class="w-full">
               <thead class="bg-slate-100 w-full h-12 border-b-2 border-slate-200">
                    <tr>
                         <th>
                              <label class="flex items-center justify-center">
                                   <input type="checkbox" class="h-full hidden" @change="checkAllItems()" />
                                   <span class="border-2 rounded-md border-slate-300 size-5 hover:cursor-pointer" :class="checkAll ? 'bg-slate-400' : 'bg-white'"></span>
                              </label>
                         </th>
                         <th class="text-slate-700 font-medium text-left">Add</th>
                         <th class="text-slate-700 font-medium text-left">Object</th>
                         <th class="text-slate-700 font-medium text-left">Company</th>
                         <th class="text-slate-700 font-medium text-left">Statue</th>
                         <th class="text-slate-700 font-medium text-left">Amount</th>
                    </tr>
               </thead>
               <tbody class="bg-slate-50 w-full">
                    <tr v-for="product in filteredProducts" :key="product.id" :class="isChecked(product.id) ? 'bg-slate-200 border-white' : 'border-slate-200'" class="h-16 border-b-2">
                         <td class="flex justify-center h-16">
                              <label class="flex items-center">
                                   <input type="checkbox" class="h-full hidden" :checked="isChecked(product.id)" @change="checkItem(product.id)" />
                                   <span class="border-2 rounded-md border-slate-300 size-5 hover:cursor-pointer" :class="isChecked(product.id) ? 'bg-slate-400' : 'bg-white'"></span>
                              </label>
                         </td>
                         <td class="h-16">{{ product.date }}</td>
                         <td class="h-16">{{ product.object }}</td>
                         <td class="h-16">
                              <div class="w-full h-full flex items-center">
                                   <img :src="displayCompanyIcon(product.company)" alt="" class="w-8 h-8 mr-3" />
                                   {{ displayCompanyName(product.company) }}
                              </div>
                         </td>
                         <td cl>
                              <span :class="`inline-block w-2 h-2 rounded-full ${displayColorStatus(product.status)}`"></span>
                              {{ displayStatus(product.status) }}
                         </td>
                         <td>{{ product.amount }}</td>
                    </tr>
               </tbody>
          </table>
     </main>
</template>

<script setup lang="ts">
import { ref, watch } from "vue"

const currentStatue = ref("all")

const products = ref([
     {
          id: 1,
          date: "Jan. 24",
          object: "Product Design : Payme",
          company: "stripe",
          company_name: "Stripe Inc.",
          status: "pending",
          amount: "7.800 $USD",
     },
     {
          id: 2,
          date: "Jan. 24",
          object: "App Redesign : Onboar",
          company: "github",
          company_name: "Github Corp.",
          status: "cancelled",
          amount: "12.800 $USD",
     },
     {
          id: 3,
          date: "Dec. 23",
          object: "Pitch Deck B2B",
          company: "amazon",
          company_name: "Amazon",
          status: "ongoing",
          amount: "14.000 $USD",
     },
     {
          id: 4,
          date: "Oct. 23",
          object: "Mobile App, UX Audit",
          company: "steam",
          company_name: "Steam",
          status: "waitingforconfirmation",
          amount: "2.000 $USD",
     },
     {
          id: 5,
          date: "Oct. 23",
          object: "Splash Screen Illustrator",
          company: "adobe",
          company_name: "Adobe LLC.",
          status: "completed",
          amount: "5.500 $USD",
     },
     {
          id: 6,
          date: "Oct. 23",
          object: "Features Add",
          company: "thebrowser",
          company_name: "The Browser Company",
          status: "pending",
          amount: "14.500 $USD",
     },
     {
          id: 7,
          date: "Sept. 23",
          object: "Brand Guidelines",
          company: "figma",
          company_name: "Figma",
          status: "completed",
          amount: "21.500 $USD",
     },
     {
          id: 8,
          date: "Sept. 23",
          object: "New messages UX",
          company: "slack",
          company_name: "Slack Inc.",
          status: "ongoing",
          amount: "1.900 $USD",
     },
     {
          id: 9,
          date: "Sept. 23",
          object: "Landing page",
          company: "opensea",
          company_name: "Opensea",
          status: "pending",
          amount: "2.300 $USD",
     },
])

const labels = ref([
     {
          id: 1,
          name: "all",
          label: "All deals",
     },
     {
          id: 2,
          name: "completed",
          label: "Completed",
     },
     {
          id: 3,
          name: "pending",
          label: "Pending",
     },
     {
          id: 4,
          name: "ongoing",
          label: "Ongoing",
     },
     {
          id: 5,
          name: "waitingforconfirmation",
          label: "Waiting for confirmation",
     },
     {
          id: 6,
          name: "cancelled",
          label: "Cancelled",
     },
])

const filteredProducts = ref(products.value)

const search = ref("")

const checkedItems: ref<number[]> = ref([])

/**
 * Display the status based on the status provided
 *
 * @param statue
 */

const displayStatus = (statue: string) => {
     switch (statue) {
          case "completed":
               return "Completed"
          case "pending":
               return "Pending"
          case "ongoing":
               return "Ongoing"
          case "waitingforconfirmation":
               return "Waiting for confirmation"
          case "cancelled":
               return "Cancelled"
          default:
               return "Unknown"
     }
}

/**
 * Display the color status based on the status provided
 *
 * @param statue
 */

const displayColorStatus = (statue: string) => {
     switch (statue) {
          case "completed":
               return "bg-blue-500"
          case "pending":
               return "bg-orange-500"
          case "ongoing":
               return "bg-green-500"
          case "waitingforconfirmation":
               return "bg-purple-500"
          case "cancelled":
               return "bg-red-500"
          default:
               return "bg-gray-500"
     }
}

/**
 * Display the company name based on the company name provided
 *
 * @param company
 */

const displayCompanyName = (company: string) => {
     switch (company) {
          case "stripe":
               return "Stripe Inc."
          case "github":
               return "Github Corp."
          case "amazon":
               return "Amazon"
          case "steam":
               return "Steam"
          case "adobe":
               return "Adobe LLC."
          case "thebrowser":
               return "The Browser Company"
          case "figma":
               return "Figma"
          case "slack":
               return "Slack Inc."
          case "opensea":
               return "Opensea"
          default:
               return "Unknown"
     }
}

/**
 * Display the company icon based on the company name provided
 *
 * @param company
 */
const displayCompanyIcon = (company: string) => {
     switch (company) {
          case "stripe":
               return "/images/stripe.png"
          case "github":
               return "/images/github.png"
          case "amazon":
               return "/images/amazon.png"
          case "steam":
               return "/images/steam.png"
          case "adobe":
               return "/images/adobe.png"
          case "thebrowser":
               return "/images/arc.png"
          case "figma":
               return "/images/figma.png"
          case "slack":
               return "/images/slack.png"
          case "opensea":
               return "/images/opensea.png"
     }
}

/**
 *
 * @param statue
 */
const filterItems = (statue: string) => {
     currentStatue.value = statue
     if (statue === "all") {
          filteredProducts.value = products.value
     } else {
          filteredProducts.value = products.value.filter((product) => product.status === statue)
     }
}

/**
 * Count the number of items with a specific status
 *
 * @param statue
 */
const countItemsStatus = (statue: string) => {
     if (statue === "all") return products.value.length
     return products.value.filter((product) => product.status === statue).length
}

const checkAll = ref(false)

const checkAllItems = () => {
     checkAll.value = !checkAll.value
     if (checkAll.value) {
          checkedItems.value = products.value.map((product) => product.id)
     } else {
          checkedItems.value = []
     }

     console.log(checkedItems.value)
}

/**
 * Check or uncheck an item based on the id provided
 *
 * @param id
 */

const checkItem = (id: number) => {
     const index = checkedItems.value.indexOf(id)

     console.log(checkedItems.value, id, index)

     if (checkedItems.value.includes(id)) {
          checkedItems.value.splice(index, 1)
     } else {
          checkedItems.value.push(id)
     }
}

console.log(checkedItems.value)

const isChecked = (id: number) => {
     if (checkedItems.value.includes(id)) return true
}

const detectKeyboardShortcut = (event: KeyboardEvent) => {
     if ((event.ctrlKey && event.key === "k") || (event.metaKey && event.key === "k")) {
          const searchInputElement = document.getElementById("search_object")
          searchInputElement.focus()
     }
}

window.addEventListener("keydown", detectKeyboardShortcut)

/**
 * Watch the search input and filter the products based on the search value
 */
watch(search, (searchTerm: string) => {
     if (searchTerm === "") {
          filteredProducts.value = products.value
     } else {
          filteredProducts.value = products.value.filter((product) => product.object.toLowerCase().includes(searchTerm.toLowerCase()))
     }
})
</script>
