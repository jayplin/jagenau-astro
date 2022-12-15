<script lang="ts" setup>
import { ref } from 'vue';
import { useNow } from '@vueuse/core'
import pkg from 'naive-ui';
const { NButton } = pkg;


const count = ref(0);
const add = () => (count.value = count.value + 1);
const subtract = () => (count.value = count.value - 1);

const now = useNow()
</script>
	
<template>
	<div class="counter">
		<NButton @click="subtract()">-</NButton>
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
