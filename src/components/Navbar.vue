<template>
  <nav class="w-72 h-full p-5">
    <span>
      <img src="/images/logo.svg" alt="">
    </span>
    <div class="mt-8 grid grid-cols-[30px_1fr_50px] h-10 items-center bg-white border-slate-200 border-solid border-2 rounded-md">
      <div class="flex w-full h-full justify-center items-center">
        <img src="/images/icons/search.png" alt="" class="w-4 h-4">
      </div>
      <input type="text" placeholder="Search" class="w-full h-full outline-none">
      <div class="flex justify-center items-center bg-slate-200 rounded-lg mr-1 p-1">
        <img src="/images/icons/macos_cmd.svg" alt="" class="mr-1">
        <span class="font-normal">K</span>
      </div>
    </div>
    <ul class="pr-3">
      <li class="text-slate-400 font-medium my-5">Navigation</li>
      <li>
        <ul>
          <li class="hover:translate-x-3 hover:bg-slate-200 flex py-2 my-1 font-bold text-slate-500 rounded-md cursor-pointer"><img class="pl-2 mr-2" src="/images/icons/home.svg" alt=""> Home</li>
          <li class="hover:translate-x-3 hover:bg-slate-200 flex py-2 my-1 font-bold text-slate-500 rounded-md cursor-pointer"><img class="pl-2 mr-2" src="/images/icons/charts.svg" alt=""> Clients</li>
          <li class="hover:translate-x-3 hover:bg-slate-200 flex py-2 my-1 font-bold text-slate-500 rounded-md cursor-pointer"><img class="pl-2 mr-2" src="/images/icons/layers.svg" alt=""> Leads</li>
          <li class="hover:translate-x-3 hover:bg-slate-200 flex py-2 my-1 font-bold text-slate-500 rounded-md cursor-pointer"><img class="pl-2 mr-2" src="/images/icons/check-done.svg" alt=""> Deals</li>
        </ul>
      </li>
      <li class="text-slate-400 font-medium my-5">Your Lists</li>
      <li>
        <ul>
          <li class="hover:translate-x-3 hover:bg-slate-200 flex py-2 my-1 font-bold text-slate-500 rounded-md cursor-pointer"><img class="pl-2 mr-2" src="/images/icons/circle_arrow_down.svg" alt=""> Inbound</li>
          <li class="hover:translate-x-3 hover:bg-slate-200 flex py-2 my-1 font-bold text-slate-500 rounded-md cursor-pointer"><img class="pl-2 mr-2" src="/images/icons/circle_arrow_up.svg" alt=""> Outbound</li>
          <li class="hover:translate-x-3 hover:bg-slate-200 flex py-2 my-1 font-bold text-slate-500 rounded-md cursor-pointer"><img class="pl-2 mr-2" src="/images/icons/check-done.svg" alt=""> Ads</li>
        </ul>
      </li>
      <li>
        <ul>
          <li class="hover:translate-x-3 hover:bg-slate-200 flex py-2 my-1 font-bold text-slate-500 rounded-md cursor-pointer"><img class="pl-2 mr-2" src="/images/icons/bell.svg" alt=""> Notifications <span class="ml-3 bg-slate-500 text-sm text-white px-5 rounded-lg">3</span></li>
          <li class="hover:translate-x-3 hover:bg-slate-200 flex py-2 my-1 font-bold text-slate-500 rounded-md cursor-pointer"><img class="pl-2 mr-2" src="/images/icons/settings.svg" alt=""> Settings</li>
        </ul>
      </li>
    </ul>
    <div class="mt-5 border-2 border-slate-200 border-solid bg-white rounded-lg px-3 gap-y-3 grid pb-3">
      <header class="flex w-full py-3 gap-x-3 font-bold text-slate-500">
        <img src="/images/icons/checks.svg" alt="">
        Deals
      </header>
      <div>
        <div class="w-full bg-slate-200 h-2 rounded-full">
          <div class="bg-black w-9/12 h-full rounded-full"></div>
        </div>
        <span class="text-sm text-slate-500 font-medium">5 Deals left from 30 Leads</span>
      </div>
      <div>
        <button class="px-5 hover:bg-slate-700 bg-slate-900 w-full text-white py-2 rounded-lg font-bold flex items-center justify-center"><img src="/images/icons/crown.svg" alt="" class="mr-3">Upgrade to pro</button>
      </div>
    </div>
    <div class="rounded-lg p-3 gap-x-3 grid grid-cols-[40px_1fr_40px] grid-rows-[20px_20px] bg-white mt-5 border-2 border-slate-200 border-solid">
      <img src="/images/user.png" alt="" class="col-start-1 row-start-1 row-end-3 ">
      <span class="text-sm row-start-1 col-start-2 font-bold text-slate-500">Arthur Bossuyt</span>
      <span class="text-sm row-start-2 col-start-2">Arthur@squared.studio</span>
      <img src="/images/icons/arrow_down.svg" alt="" class="row-start-2 col-start-3">
    </div>
  </nav>
</template>
<script setup lang="ts">
</script>
