<template>
    <div class="bg-gray-800 py-5 text-center text-white absolute bottom-0 w-full">
      <div class="flex flex-col">
        <span>
          Made with
          <Icon name="material-symbols:favorite-rounded" color="crimson" /> copyright (2023 -{{ date }})
        </span>
      </div>
    </div>
  </template>
  
  <script setup>
  const date = new Date().getFullYear();
  </script>