<template>
  <div id="app">
    <TheHeader />
    <TheTitle />
    <router-view />
  </div>
</template>

<script>
import TheHeader from '@/layouts/TheHeader.vue'
import TheTitle from '@/layouts/TheTitle.vue'

export default {
  name: 'App',
  components: {
    TheHeader,
    TheTitle
  }
}
</script>

<style scoped>
input[type="text"], input[type="password"] { 
  outline: none; 
}

@import url('https://fonts.googleapis.com/css?family=Noto+Sans+KR|Nunito&display=swap');

* {
  font-family: 'Noto Sans KR', sans-serif;
}

/* font-family: 'Nunito', sans-serif; */
</style>
