<script setup>
  import { ref } from 'vue';
  
  const text = ref('');
  const barras = ref([
	{ color: 'bg-gray-300' },
	{ color: 'bg-gray-300' },
	{ color: 'bg-gray-300' },
	{ color: 'bg-gray-300' },
	{ color: 'bg-gray-300' },
  ]);
  
  const countWords = () => {
	const wordCount = text.value.trim().split(/\s+/).length;
	actualizarBarras(wordCount);
  };
  
  const actualizarBarras = (count) => {
	let colors = [];
	if (count >= 7) {
	  colors = ['bg-red-500', 'bg-orange-500', 'bg-yellow-500', 'bg-green-500', 'bg-green-500'];
	} else if (count >= 5) {
	  colors = ['bg-red-500', 'bg-orange-500', 'bg-yellow-500', 'bg-yellow-500', 'bg-gray-300'];
	} else if (count >= 3) {
	  colors = ['bg-red-500', 'bg-orange-500', 'bg-orange-500', 'bg-gray-300', 'bg-gray-300'];
	} else if (count >= 1) {
	  colors = ['bg-red-500', 'bg-red-500', 'bg-gray-300', 'bg-gray-300', 'bg-gray-300'];
	} else {
	  colors = ['bg-gray-300', 'bg-gray-300', 'bg-gray-300', 'bg-gray-300', 'bg-gray-300'];
	}
	barras.value = barras.value.map((bar, index) => ({ color: colors[index] || 'bg-gray-300' }));
  };
  </script>
  
  <template>
	<div class="flex flex-col items-center mt-10">
	  <div class="flex space-x-2">
		<div v-for="(bar, index) in barras" :key="index" :class="bar.color" class="h-16 w-8 rounded"></div>
	  </div>
	  <textarea v-model="text" @input="countWords" class="mt-4 p-2 border rounded w-64" rows="2"></textarea>
	</div>
  </template>