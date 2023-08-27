<template>
  <div>
    <svg-icon icon-class="github" @click="goto" />
  </div>
</template>

<script setup>
const url = ref('https://github.com/Mhist/RuoYi-Vue3/');

function goto() {
  window.open(url.value)
}
</script>
