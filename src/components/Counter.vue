<script lang="ts" setup>
import { ref } from 'vue';
import { useNow } from '@vueuse/core'
import { NButton } from 'naive-ui'



const count = ref(0);
const add = () => (count.value = count.value + 1);
const subtract = () => (count.value = count.value - 1);

const now = useNow()
</script>
	
<template>
	<div class="counter">
		<n-button @click="subtract()">-</n-button>
		<pre>{{ count }}</pre>
		<button @click="add()">+</button>
		{{ now }}
	</div>
	<div class="counter-message">
		<slot />
	</div>
</template>


<style>
.counter {
	display: grid;
	font-size: 2em;
	grid-template-columns: repeat(3, minmax(0, 1fr));
	margin-top: 2em;
	place-items: center;
}

.counter-message {
	text-align: center;
}
</style>
