<script setup lang="ts">
</script>

<template>
  <main class="bg-white p-8 w-full m-5 border-2 border-slate-200 border-solid rounded-xl">
    <header>
      <h1 class="text-5xl font-bold text-slate-700">Deals</h1>

      <nav>
        <ul class="flex mt-5 font-medium">
          <li class="px-5 border-b-2 border-black cursor-pointer">All Deals</li>
          <li class="cursor-pointer hover:text-slate-500 text-slate-300 px-5 border-b-2 border-slate-300">Completed (3)</li>
          <li class="cursor-pointer hover:text-slate-500 text-slate-300 px-5 border-b-2 border-slate-300">Pending (10)</li>
          <li class="cursor-pointer hover:text-slate-500 text-slate-300 px-5 border-b-2 border-slate-300">Ongoing (2)</li>
          <li class="cursor-pointer hover:text-slate-500 text-slate-300 px-5 border-b-2 border-slate-300">Waiting for confirmation (1)</li>
        </ul>
        <ul class="flex justify-between">
          <li>
            <ul class="flex items-center gap-x-3">
              <li>
                <div class="grid grid-cols-[30px_1fr_50px] h-10 items-center bg-white border-slate-200 border-solid border-2 rounded-md">
                  <div class="flex w-full h-full justify-center items-center">
                    <img src="/images/icons/search.png" alt="" class="w-4 h-4">
                  </div>
                  <input type="text" placeholder="Search" class="w-full h-full outline-none">
                  <div class="flex justify-center items-center bg-slate-200 rounded-lg mr-1 p-1">
                    <img src="/images/icons/macos_cmd.svg" alt="" class="mr-1">
                    <span class="font-normal">K</span>
                  </div>
                </div>
              </li>
              <li class="text-slate-400 font-medium my-5">
                <button class="px-4 h-10 gap-x-3 border-2 border-slate-200 border-solid w-fit hover:bg-slate-100 text-black bg-white w-full rounded-lg font-medium flex items-center justify-center">
                  <span class="text-slate-500">Object</span> <img src="/images/icons/arrow_down.svg" alt="" class=""></button>
              </li>
              <li class="text-slate-400 font-medium my-5">
                <button class="px-4 h-10 gap-x-3 border-2 border-slate-200 border-solid w-fit hover:bg-slate-100 text-black bg-white w-full rounded-lg font-medium flex items-center justify-center">
                  <span class="text-slate-500">Company</span> <img src="/images/icons/arrow_down.svg" alt="" class=""></button>
              </li>
              <li class="text-slate-400 font-medium my-5">
                <button class="px-4 h-10 gap-x-3 border-2 border-slate-200 border-solid w-fit hover:bg-slate-100 text-black bg-white w-full rounded-lg font-medium flex items-center justify-center">
                  <span class="text-slate-500">Statue</span> <img src="/images/icons/arrow_down.svg" alt="" class=""></button>
              </li>
            </ul>
          </li>
          <li>
            <ul class="flex items-center gap-x-5">
              <li>
                <button class="px-4 h-10 gap-x-3 border-2 border-slate-200 border-solid w-fit hover:bg-slate-200 bg-white w-full rounded-lg font-medium flex items-center justify-center">
                  <img src="/images/icons/share.svg" alt="" class="">
                  <span class="text-black">Export</span> </button>
              </li>
              <li class="text-slate-400 font-medium my-5">
                <button class="px-4 h-10 gap-x-3 border-2 border-slate-200 border-solid w-fit hover:bg-slate-700 bg-slate-800 w-full rounded-lg font-medium flex items-center justify-center">
                  <img src="/images/icons/new_folder.svg" alt="" class="">
                  <span class="text-white">New Deal</span> </button>
              </li>
            </ul>
          </li>
        </ul>
      </nav>
    </header>

  </main>
</template>
