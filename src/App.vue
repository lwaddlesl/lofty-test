<template>
  <div>
    <HeaderComponent />
    <div class="flex">
      <div v-for="i in 6">
        <div class="items"></div>
      </div>
    </div>
  </div>
</template>

<script>
import HeaderComponent from './components/HeaderComponent.vue'

export default {
  name: 'App',
  components: {
    HeaderComponent
  }
}
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
html {
  margin: 0;
  padding: 0;
  background-color: rgb(43, 42, 53);
}
.flex {
  display: flex;
  flex-wrap: wrap;
  margin-left: 20px;
}
.items {
  margin: 20px 20px 0 0;
  width: calc(33.33vw - 26.67px);
  height: 200px;
  background-color: gray;
}
@media screen and (max-width: 1023px) {
  .items {
    width: calc(50vw - 30px);
  }
}
@media screen and (max-width: 767px) {
  .items {
    width: calc(100vw - 40px);
  }
}
</style>
