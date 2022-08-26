<script setup>
import { ref } from "vue";
import { invoke } from "@tauri-apps/api/tauri";

const greetMsg = ref("");
const name = ref("");

async function greet() {
  greetMsg.value = await invoke("greet", { name: name.value });
}
</script>

<template>
  <div class="card">
    <input v-model="name" placeholder="Introduce tu nombre..." />
    <button type="button" @click="greet()">Saludar</button>
  </div>

  <p>{{ greetMsg }}</p>
</template>
