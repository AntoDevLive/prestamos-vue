<script setup>
  import { ref, computed } from 'vue';
  import Header from './components/Header.vue';
  import Button from './components/Button.vue';

  const cantidad = ref(10000);

  const MIN = 0;
  const MAX = 20000;
  const STEP = 100;

  const formatearDinero = computed(() => {
    const formatter = new Intl.NumberFormat('en-US', {
      style: 'currency',
      currency: 'USD'
    });

    return formatter.format(cantidad.value);
  });

  const handleChangeDecremento = () => {
    if(cantidad.value - STEP < MIN) {
      alert('cantidad no válida')
      return;
    }
    cantidad.value = cantidad.value - STEP;
  }

  const handleChangeIncremento = () => {
    if(cantidad.value + STEP > MAX) {
      alert('cantidad no válida')
      return;
    }
    cantidad.value = cantidad.value + STEP;
  }

</script>


<template>
  <div className="my-20 max-w-lg mx-auto bg-white shadow p-10">
    <Header />

    <div className="flex justify-between my-6">
        <Button 
          :operador="'-'"
          :fn="handleChangeDecremento"
        />
        <Button 
          :operador="'+'"
          :fn="handleChangeIncremento"
        />
    </div>

    <div class="my-5">
      <input
          type="range"
          className="w-full h-6 bg-gray-200 accent-lime-500 hover:accent-lime-600"
          :min="MIN"
          :max="MAX"
          :step="STEP"
          v-model.number="cantidad"
      />

     <p class="text-center my-10 text-5xl font-bold text-indigo-600">{{ formatearDinero }}</p> 
    </div>

  </div>
</template>