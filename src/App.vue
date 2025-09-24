<script setup>
  import Header from './components/Header.vue';

  function handleChange(e) {
    console.log(e.target.value)
  }
</script>

<template>
  <div className="my-20 max-w-lg mx-auto bg-white shadow p-10">
    <Header />

    <div class="my-5">


      <input
          type="range"
          className="w-full h-6 bg-gray-200 accent-lime-500 hover:accent-lime-600"
          @input="handleChange"
          
      />
    </div>

  </div>
</template>