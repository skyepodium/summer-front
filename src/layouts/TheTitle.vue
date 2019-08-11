<template>
  <div
    class="wrapper" 
    :style="{ 'background-image': 'url(' + mainUrl + ')' }"
  />
</template>

<script>
import mainUrl from '@/assets/summer.jpg'

export default {
    name: 'TheTitle',
    data () {
        return {
            mainUrl: mainUrl
        }
    }
}
</script>

<style scoped>
.wrapper {
    width: 100%;
    height: 200px;
    background-color: rgb(79, 44, 250);
    overflow: hidden;
    background-position: center;
    -webkit-background-size: cover;
    -moz-background-size: cover;
    -ms-background-size: cover;
    -o-background-size: cover;
    background-size: cover;
}
</style>