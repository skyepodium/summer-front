<template>
  <div class="wrapper">
    <div class="inner">
      <router-link
        to="/"
        class="logo"
      >
        SUMMER
      </router-link>
      <router-link
        to="/"
        class="auth"
      >
        로그인
      </router-link>
    </div>
  </div>
</template>

<script>
export default {
    name: 'TheHeader'
}
</script>

<style scoped>
.wrapper{
  width: 100%;
  height: 50px;
  line-height: 50px;
  border-bottom: 1px solid #ececec;
}

.inner {
  width: calc(100% - 40px);
  margin-left:auto;
  margin-right:auto;
  height: inherit;
  line-height: inherit;
}

.logo {
  display: block;
  text-decoration: none;
  float:left;
  color: black;
  font-size: 25px;
  font-family: 'Nunito', sans-serif;
}

.auth { 
  display: block;
  text-decoration: none;
  float:right;
  color: white;
  font-size: 18px;
  padding-left: 10px;
  padding-right: 10px;
  height: 38px;
  line-height: 38px;
  margin-top: 6px;
  border-radius: 4px;
  box-sizing: border-box;
  background-color: rgb(79, 44, 250);
}
</style>